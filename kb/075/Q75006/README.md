---
layout: page
title: "Q75006: Virtual Communications Driver Functional Structure"
permalink: /kb/075/Q75006/
---

## Q75006: Virtual Communications Driver Functional Structure

{% raw %}

	Article: Q75006
	Product(s): Microsoft Windows Device Driver Kit
	Version(s): 3.0,3.1,3.11
	Operating System(s): 
	Keyword(s): kb16bitonly kbDDK
	Last Modified: 30-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Device Development Kit (DDK) for Windows, versions 3.0, 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In the Microsoft Windows graphical environment, the virtual communications
	driver (VCD) is the virtual device (VxD) that "virtualizes" COM ports. Its main
	role is to arbitrate COM port use between virtual machines (VMs). This article
	discusses the various functions of the VCD and the routines that it uses.
	
	MORE INFORMATION
	================
	
	The VCD is the ring 0 interrupt handler for COMM.DRV, the Windows communication
	driver, in the system VM. The VCD arbitrates COM port contention, by tracking
	port ownership. When Windows starts, VCD traps input and output for every COM
	port, which allows VCD to monitor all I/O activity from every VM. Under Windows
	3.0, if a VM enables interrupts for a COM port, or attempts to output data, then
	VCD determines that the VM should own the port and attempts to assign ownership,
	or it displays a message box informing the user of the contention.
	
	The functions of the VCD are listed below by category.
	
	Initialization
	--------------
	
	VCD_Sys_Crit_Init, VCD_Device_Init, VCD_Init_Complete, and VCD_Init_Port
	initialize VCD.
	
	VCD_Sys_Crit_Init attempts to read base and IRQ specifications from the
	SYSTEM.INI file.
	
	VCD_Device_Init calls VCD_Init_Port to allocate memory for each COM port and to
	read its initial state. VCD_Device_Init also instances COM-related data
	structures in the BIOS data area and hooks the Interrupt 14h chain to enable VCD
	to process an Interrupt 14h before any virtual 8086 mode
	terminate-and-stay-resident programs (V86 TSRs) or device drivers do.
	
	VCD_Create_VM, VCD_Init_VM_CB, and VCD_Set_IRQ_Procs initialize the COM
	structures VCD maintains for each VM. For each COM port in the system, VCD
	allocates and maintains a separate chunk of control block memory for each VM.
	VCD_Init_VM_CB initializes the control block structure for one COM port.
	VCD_Create_VM calls VCD_Init_VM_CB for each COM port. VCD_Set_IRQ_Procs sets up
	pointers to handler routines for IRQ processing; this is required to support
	port virtualization when another VxD wants to virtualize a COM port. When this
	happens, VCD cooperates and assists the other VxD.
	
	Port Handling
	-------------
	
	Port handling refers to a group of routines that maintain ownership of a COM
	port.
	
	VCD_Attach and VCD_Detach save and restore the state of the I/O ports that
	control a COM port.
	
	VCD_Enable_Trapping and VCD_Disable_Trapping enable and disable I/O port trapping
	for a COM port.
	
	VCD_Set_Owner_Event is an event procedure that sets up register parameters for
	calling into VCD_Set_Owner. If a VCD receives a hardware interrupt and the
	corresponding port is not currently owned, then VCD schedules an event to assign
	the port to the current VM.
	
	VCD_Set_Owner calls VCD_Attach and VCD_Detach as necessary to assign a COM port
	to a VM.
	
	VCD_Assign performs contention processing. When VCD detects that a new VM wants
	to own a port, VCD calls VCD_Assign. VCD_Assign first checks to see if the port
	is owned. If not, it can assign the port; otherwise, it must determine what
	should be done about the contention.
	
	VCD_Virtualize_IRQ is called the first time that a COM port is assigned. It calls
	the virtual programmable interrupt controller device (VPICD) to virtualize the
	IRQ that the COM port uses.
	
	Port Trapping
	-------------
	
	The routines VCD_Trap_COM1, VCD_Trap_COM2, VCD_Trap_COM3, and VCD_Trap_COM4 are
	the front-line routines that trap the I/O ports that correspond to a COM port.
	Each routine sets the ESI register to point to the correct COM data structure
	and drops into VCD_Dispatch_IO.
	
	VCD_Dispatch_IO determines how to handle the I/O. In some cases it just handles
	it virtually by saving the written data or by returning the current virtual
	state. VCD_Dispatch_IO can also perform physical I/O if the port is already
	owned, and it can call VCD_Assign to assign the port.
	
	The individual routines for the virtual I/O are:
	
	VCD_Virt_In_Out_RxTxB, VCD_Virt_In_Out_IER, VCD_Virt_In_IIR, VCD_Virt_In_LCR,
	VCD_Virt_Out_LCR, VCD_Virt_In_MCR, VCD_Virt_Out_MCR, VCD_Virt_In_LSR, and
	VCD_Virt_In_MSR. These routines handle INs and OUTs for a single I/O port
	associated with a COM port.
	
	Miscellaneous
	-------------
	
	VCD_Control is the control procedure that is required in every VxD to handle
	system control broadcasts (see System_Control service in Chapter 33 of the
	"Microsoft Windows Device Development Kit Virtual Device Adaptation Guide").
	
	VCD_Set_Focus forces ownership of "global" COM ports to the current VM. This
	service is most often used for a serial mouse, so that COM interrupts go to the
	VM that has the focus and, therefore, owns the mouse.
	
	VCD_Suspend_VM calls VCD_Clear_Int to clear any outstanding interrupts for a COM
	port when its owner VM is suspended.
	
	VCD_Notify_VxD notifies another VxD about state changes for a COM port that has
	been virtualized with the VCD_Virtualize_Port service.
	
	VCD_Destroy_VM calls VCD_Detach through VCD_Detach_If_Owner for any COM ports
	owned by the VM that is being destroyed.
	
	VCD_Soft_Int_14h monitors Interrupt 14h calls and records the current system time
	as an indication of "last use;" this time is used to determine if a port can be
	stolen when contention is detected.
	
	Interrupt Processing
	--------------------
	
	VCD_Int_for_1, VCD_Int_for_2, VCD_Int_for_3, and VCD_Int_for_4 are the front-line
	routines called by VPICD when a hardware interrupt for a COM port requires
	service. Each routine sets up ESI to point to the correct COM data structure and
	then jumps to the actual handler.
	
	VCD_VirtInt_For_1, VCD_VirtInt_For_2, VCD_VirtInt_For_3, and VCD_VirtInt_For_4
	are all similar to VCD_Int_for_x, but handle VPICD calls for virtual interrupts
	simulated into a VM.
	
	VCD_EOI_for_1, VCD_EOI_for_2, VCD_EOI_for_3, and VCD_EOI_for_4 are also similar,
	but handle VPICD calls for when a VM executes an EOI instruction to end
	processing of a COM port's simulated interrupt.
	
	VCD_Mask_for_1, VCD_Mask_for_2, VCD_Mask_for_3, and VCD_Mask_for_4 are also
	similar and handle VPICD calls for when a VM masks or unmasks a COM port's IRQ.
	
	VCD_IRET_For_1, VCD_IRET_For_2, VCD_IRET_For_3, and VCD_IRET_For_4 are also
	similar and handle VPICD calls for when a VM returns from a simulated interrupt
	(IRET).
	
	VCD_Sharable_Int is the default hardware interrupt handler when a COM port's IRQ
	is shared with another device in the system, including another COM port.
	VCD_Sharable_Int reads and records the interrupt identification register for the
	port and checks to see if the port has requested an interrupt. If the port has
	requested an interrupt, then it falls into VCD_Int. If not, it chains the
	interrupt to the next handler.
	
	VCD_Int is the default hardware interrupt handler. VCD_Int determines if
	ownership needs to be assigned, in which case it schedules an event; otherwise,
	it requests a virtual interrupt into the owner VM by calling VPICD.
	
	VCD_Sharable_EOI and VCD_EOI watch for the VM to enable an interrupt and boost
	the execution time of the VM to give it some extra time to process the
	interrupt.
	
	VCD_Mask is the default mask handler that is called when a VM masks or unmasks a
	COM port IRQ. VCD_Mask calls VCD_Assign to attempt to assign ownership of the
	COM port to the current VM.
	
	VCD_Xmit_CallBack, VCD_Enable_THRE, VCD_Sharable_COMM_Int, VCD_COMM_Int,
	VCD_LineStat, VCD_DataAvail, VCD_XmitEmpty, VCD_ModemStatus, and
	VCD_Eat_Interrupt essentially duplicate the functionality of the interrupt
	handler built into COMM.DRV. This duplication provides a 32-bit ring 0 interrupt
	handler to an application developed for Windows through the standard Windows
	COMM interface and significantly improves the performance of enhanced mode
	Windows.
	
	Services
	--------
	
	The VCD_Virtualize_Port service provides a way for another VxD to claim
	virtualization ownership of a COM port. The VxD can then handle trapped I/O and
	hardware interrupts. VCD passes interrupts to this other VxD, maintains port
	ownership state information, and handles contention between VMs.
	
	VCD_Get_Version returns a VxD implementation version number.
	
	VCD_Set_Port_Global is called by the virtual mouse driver (VMD) to indicate that
	the COM port used by the mouse should be considered global and to disable
	contention checking.
	
	VCD_Get_Focus determines the current owner of a COM port.
	
	Protected Mode Functions (Mainly Provided for COMM.DRV Interface)
	-----------------------------------------------------------------
	
	A function in VCD enables COMM.DRV and the Windows Control Panel to send data to
	VCD.
	
	VCD_PM_Get_Version returns the current implementation version.
	
	VCD_PM_Get_Port_Array returns an array of available COM ports.
	
	VCD_PM_Get_Port_Behavior returns the current value of the "auto assign" time
	limit used to determine how to handle contention.
	
	VCD_PM_Set_Port_Behavior allows the Control Panel to modify the "auto assign"
	value for a COM port.
	
	VCD_PM_Acquire_Port and VCD_PM_Free_Port are used by COMM.DRV to enable and
	disable the special ring 0 interrupt handler implemented in the VCD.
	
	Debugging
	---------
	
	VCD_Debug_Dump and VCD_Dump2 are available in the debugging version of VCD. These
	routines dump a few of the internal data structures maintained by VCD.
	
	NOTE: For a detailed description of the communications driver functional
	structure of Windows for Workgroups 3.11, please refer to the document VCOMM.DOC
	in the DDK.
	
	Additional query words: 3.00 3.10 3.11 3.x COMM DDKVCD
	
	======================================================================
	Keywords          : kb16bitonly kbDDK 
	Technology        : kbAudDeveloper kbWin3xSearch kbWinDDKSearch kbWinDDK300 kbWinDDK310 kbWinDDK311
	Version           : :3.0,3.1,3.11
	
	=============================================================================
	

{% endraw %}
