# Test 5. Motherboard. Non-volatile Storage. ROM and booting

# Motherboard

The computer parts discussed so far — CPU, RAM dies, the BIOS die — are physically located on the **motherboard**. It is, as the name suggests, the place for attaching the most important components. Besides just hosting them, it enables them to communicate with each other.

On the modern motherboard, we can find the following elements:  

* a CPU slot (or _socket_) — a place to put a CPU in (though it also happens that the CPU is soldered directly to the motherboard);

* RAM slots: typically DDR3, DDR4, DDR5 (here, it may also happen that memory is soldered directly to the motherboard<sup>1</sup>);

* the chipset (which will be discussed below);

* the BIOS die;

* the system clock generator, allowing synchronization between various components;

* power sockets, through which all the computer components are powered with electricity;

* hard drive slots;

* optical drive (CD/DVD) slots;

* keyboard slots;
  
* extension card slots (it is through them that we can connect a graphics card or a network card, or a USB port controller).

In practice, a motherboard can look as follows:

Figure 1\. A Dell Precision T3600 motherboard (from year 2012).
(Source: http://en.wikipedia.org)

1 This happens e.g. for the LPDDR memory, which is used mainly in mobile devices (phones, tablets), though also in certain laptops. This memory kind is slower and more expensive than typical DDR but in reward it requires lower voltage, which allows longer operation on battery power.

Such organization of the board with standardized sockets/slots allows for some elasticity in choosing the components to be placed inside or attached to the computer. Unfortunately, even if a component can be attached physically, it's still not guaranteed that it will be supported correctly by the motherboard and the processor. Hence, it's essential to verify compatibility specifications on every hardware upgrade.

## Chipset

A **chipset** is literally “a set of (co-operating) integrated circuits". In the case of the motherboard chipset, we can distinguish (or rather “used to distinguish", though the recent changes will be discussed later) two such circuits, called the **northbridge** and the **southbridge**. These are the chips implementing the connection between the processor and the I/O devices. The basic layout of this two-bridge system is shown below:


Figure 2\. A motherboard chipset with the two-bridge architecture.

As we see, the northbridge is located physically closer to the CPU. This is important, as it connects the components requiring the quickest access to the memory. In the early motherboards with the two-bridge structure (e.g. in the CS8220 chipset, which introduced a component called “northbridge" in 1986), the northbridge used to also contain a memory controller connected to memory buses. In the more modern solutions, as we mentioned above, these have been integrated into the processor.

The southbridge is not connected to the processor directly, but via the northbridge. That one connects — directly or indirectly — the processor to all the other (slower) input/output circuits.

In the most modern solutions, the tasks served so far by the northbridge have been taken over by the processor. This looks as follows:



Figure 3\. A motherboard chipset with the one-bridge architecture.

Even in the basic descriptions above, we can see that computer components can be:

* separate integrated circuits,
* integrated into the motherboard,
* integrated into the processor.

From a user’s perspective, these differences are not noticeable unless a part needs replacement. Higher integration can lead to more expensive repairs and harder hardware replacement if components fail. However, it usually results in better efficiency. 

Therefore, we can expect future shifts in computer architecture, with various components being integrated differently (just like the northbridge and, earlier, the RAM controller).

## Buses

Buses play a key role on the above diagrams: they transmit signals between I/O devices, the chipset, and the processor. Their bandwidth capacity and transfer speed is one of the crucial points for the overall computer efficiency.

Currently, the standard for high-speed data busses is PCI Express. It allows transmission in both directions at once (full duplex). Transmission takes place on multiple lines, which allows sending simultaneously multiple bits in one direction. The newest version offer in total a bandwidth of tens of gigabytes per second. However, not every input/output device needs so high bandwidth; therefore the southbridge is also connected to buses in many other standards. We will touch the topic of buses again when discussing the input/output system.

# Non-volatile storage

# Non-Volatile Memory: Mass Storage

So far, we've focused on primary memory. Now, let's discuss the most important type of non-volatile memory: mass storage (including hard drives, SSDs, and external memory devices like CDs/DVDs or USB drives). While theoretically a computer can function without this type of memory (operating in a mode where it receives programs from the network and prints output directly), this is very uncommon in practice. Typically, personal or office computers come with built-in mass storage, commonly referred to as a drive or disk, which is considered one of the fundamental components of a computer.

## Storage Drives

Below, we’ll discuss two main kinds of large storage devices: HDD and SSD drives.

### A Note on Terminology

Before diving into the details, let's clarify some common terminology. There is often confusion between the phrases *drive*, *disk*, *hard drive*, and *hard disk*. Although they differ in meaning, these terms are often used interchangeably in common language.

- **Drive**: Defined by the Cambridge Dictionary as “a device for storing computer information.”
- **Disk**: Refers to the actual data container, typically flat and round.

In the 1990s, we would insert a floppy disk (a data container) into a floppy disk drive (a device). Similarly, we stored files on a hard disk (a metal platter) inside a hard disk drive. Over time, “hard disk drive” became synonymous with large secondary memory, even after the introduction of solid-state drives that contain no disks. Furthermore, optical data containers are often referred to with the British spelling: “DVD disc.”

### Hard Disk Drives (HDD)

The hard disk drives (HDD) are based on magnetic storage, where information is represented by the local magnetic field of the data container. Each cell can create a permanent magnetic field encoded in binary form. The actual encoding is more complex, ensuring frequent changes in orientation to average out the total magnetic field. An electromagnetic head writes and reads the data by modifying and detecting the magnetization of the disk.

#### Physical Structure

In HDDs, data is stored on flat, round carriers called platters. A single HDD may have multiple platters rotating at high speeds, typically 7,200 rpm (or 120 revolutions per second), although cheaper models can have 5,400 rpm. Data is stored along concentric paths called tracks.

![Figure 1. An internal view of a HDD drive from the late 1990’s.](http://en.Wikipedia.org)

![Figure 2. A diagram of a HDD drive structure and its communication with the computer.](#)

#### Capacity and Limitations

The capacity of an HDD depends on the number of tracks and the density of information on each track. Magnetic effects and the need to prevent unintentional flipping of magnetic orientations limit the size and density of memory cells. Older technologies used longitudinal recording, but modern HDDs employ perpendicular recording for higher density and capacity.

#### Data Organization

Data on an HDD is accessed through read/write heads placed above a moving arm, making the physical placement of data crucial for access time. Data is read or written in chunks called sectors, typically 512 B or 4 KiB in size, each containing metadata for operational control, including checksums for error detection.

### Solid-State Drives (SSD)

SSD drives are based on semiconductor flash memory, specifically floating-gate transistors (FGT) capable of retaining an electric charge long-term. Unlike HDDs, SSDs have no moving parts, allowing for higher data access speeds and better resistance to physical damage. However, SSDs are significantly more expensive.

#### Multi-Level Cell (MLC) Technology

SSDs in home computers often use MLC technology, where each cell can hold more than two states, typically four (2 bits), eight (3 bits), or sixteen levels (4 bits). This reduces costs but increases the chance of errors and shortens the drive’s lifespan.

### External Drives

Personal computer users also widely employ external drives, which are made using HDD or SSD technology just like the internal drives discussed above but are placed outside the computer case and can be plugged in as needed, typically via USB ports. Their obvious advantage is an increase in total available secondary memory; another clear gain is portability.

These drives can also be used as data backups for internal HDD or SSD drives, as both technologies involve a risk of data corruption or loss. However, one needs to be cautious with flash memory: although it is labeled as non-volatile, it can lose its content over time due to the discharging of its internal capacitors if not used for a few years.
### Other Storage Media

#### USB Memory

Devices known as USB sticks or pen-drives (though the latter name is officially registered by a Taiwanese company Add On Technology, so it specifically applies only to their products) store data in semiconductor flash memory, just like SSD drives. The difference is that they are designed to be external, small, and portable. As a result, they are significantly slower—the limit set by the standard is 4.6 Gb/s, though in practice this speed is rarely achieved. Additionally, they are more error-prone and more expensive per byte compared to SSD drives.

#### SD Memory Cards

Another type of semiconductor flash memory, SD memory cards, is used mainly in photo and video cameras, as well as in mobile phones.

#### Optical Memory

Optical memory devices, such as CDs, DVDs, and Blu-ray discs, use a laser beam for reading and writing data. The data carrier is a surface—typically in the shape of a disk—covered with a material whose transparency can be easily changed, introducing two types of points: reflecting and non-reflecting, which represent bit values. Similar to HDD drives, the reading and writing processes in optical memory involve disk rotation to position the read/write head above the appropriate sector. The data-carrying materials can support either single or multiple writes, and they vary by total capacity:

- For the CD standard, the typical capacity is around 1 GB.
- For DVDs, the typical capacity is 4.7 GB; by using double-layered and/or double-sided discs, capacity can reach up to 17.1 GB, though such large DVDs are rarely used.
- In Blu-ray technology, the typical capacity of a disc is 25 GB. More than two layers can be supported, although this is also uncommon. The increase in information density in Blu-ray technology is achieved by using a laser beam with a shorter wavelength (blue light).

### Drive Interfaces

Besides the manufacturing technology, an important factor for the practical efficiency of a storage drive—and its usefulness in combination with a particular computer—is the way in which it is connected, that is, the type of bus and plug used.

#### Bus types

Types of buses used to connect storage drives to the processor include:

Currently, in home applications, three main types of buses are used to connect storage drives to the processor:

- **SATA (Serial ATA, where ATA stands for Advanced Technology Attachment):** Practically the only choice for HDD drives; also used for many SSD models.
- **PCIe (PCI Express, where PCI stands for Peripheral Component Interconnect):** A standard we have already encountered in the lecture "Motherboard" (due to its role in connecting the CPU to the RAM memory); also used for faster SSD models.
- **USB (Universal Serial Bus):** Mainly used for attaching external drives.

The SATA bus is derived from an older ATA model, designed specifically for communication with hard drives. For example, its cooperation with the drive controller enables the so-called native command queuing, which allows altering the order of executed read and write commands to minimize their total execution time. (Recall that this time depends on the physical placement of data on the disk, so it's beneficial to rearrange the commands so that those involving neighboring sectors are executed next to each other.) This makes SATA a proper choice for HDD drives; in turn, it is beneficial for SSD manufacturers to support that standard as well, as it allows end users to replace an older HDD with a newer SSD in a typical computer.

On the other hand, limitations in transmission speed for the SATA standard (3 Gb/s in SATA 2 and 6 Gb/s in SATA 3) make it too slow for the fastest currently available SSD drives. Therefore, fully utilizing such devices requires connecting them to a faster PCIe bus (where the analogous limit in the fastest version is nearly 1 Tb/s as of 2022, and doubles every few years).

USB stands out from the other two standards in that it was designed from the start for external devices (hence we will find USB ports on the outside of a computer case).

It's also worth mentioning that all three standards involve not only data transmission but also supplying the connected devices with an appropriate amount of electric power.

#### Communication Modes

All the above bus types are described as serial, which essentially means that transmission happens sequentially, bit by bit. It might seem that a relatively easy and effective idea for increasing the transmission rate could be switching to a parallel approach, where multiple bits would be sent at once (or more precisely: in each bus cycle, 1 bit would be sent along every wire). However, since around 2000, we've observed a transition from older parallel solutions (PCI, ATA) to serial ones (USB, SATA, PCIe). This shift occurred because mutual interference between the wires and slight differences in transmission times along them complicated synchronization on the receiving side, limiting the frequency of cycles in parallel buses. By migrating to serial transmission, we achieved significantly higher frequencies.

On the other hand, despite the term "serial," modern buses also consist of several wires. In the SATA standard, which is simplest in this regard, we have 7 wires, out of which 3 transmit no data (serving just as isolation layers for the others), and the remaining 4 wires are split into 2 pairs, each responsible for transmission in one direction. In each pair, one of the wires is a strict "negation" of the other, always transmitting the opposite bit values. In exchange for this "waste" of bandwidth, we gain clearer signal interpretation on the receiving side, a chance to detect errors in communication, and a constant level of the electric charge on both sides of the bus.

The PCIe buses, as already mentioned in the lecture "Motherboard," go much further by introducing multiple lanes, each of which allows transmitting 1 bit in each direction. In practice, each such lane consists of 4 wires, organized into two negation pairs, similar to SATA. In version 6.0, using 16 such lanes of transmission rate 60 Gb/s each allows achieving nearly 1 Tb/s in total. A similar solution—introducing 2 lanes of communication—has also been introduced in the newest versions of USB.

If so, one might ask: why is PCIe still called serial? The reason, at least partially, is that each PCIe lane operates as an independent serial connection, with its own timing for receiving subsequent bits, without the synchronization known from parallel buses. Instead, if needed, PCIe controllers perform buffering of data incoming via various lanes and join them into complete data afterward. This means that, to ensure no exhaustion of those buffers, the protocol must still involve some rough synchronization between the lanes by means of dedicated control messages. However, this technique has a much smaller impact on the overall transmission rate.

### Transmission Tax

Thanks to adopting the serial approach, modern buses do not require providing a separate clock signal: the timing of arriving bits is essentially known upfront, and potential divergences can be detected by just observing the data stream. However, this solution could cause trouble in the case of a long series of bits of the same value (e.g., if 1,000 "1"s were received in a row, there would be uncertainty if, by some chance, there were one more or one less). To address that, all buses discussed here employ a type of encoding that guarantees periodic changes in the stream content.

The oldest variant of such encoding, used in SATA and older versions of PCIe and USB, is the 8b/10b encoding. It transforms sequences of 8 bits into 10-bit representations in such a way that the resulting stream of bits never contains more than 5 identical values in a row. The price to be paid, however, is "wasting" as much as 20% of the total throughput. For example, in the case of SATA, the typically described maximum rate of 6 Gb/s does not take this effect into account; therefore, the actual maximum throughput for meaningful data is smaller by 20%.

An additional benefit of the 8b/10b encoding is that it acts as a checksum, allowing the detection of cases where a single bit has been corrupted.

In newer PCIe and USB buses, updated versions of this encoding with a lower transmission tax are utilized, such as 128b/130b encoding, which uses just 2 additional bits for every 130 bits. This method, however, requires better control of timing on the controller side. In the PCIe 6.0 standard, yet another encoding method is used: 242B/256B. This method again comes with a higher tax, but in exchange, it includes an error correction code—a more advanced system of checksums that allows not only the detection of corrupted bits but also the correction of such errors.

#### Compatibility

All the aforementioned types of buses have evolved over the years, introducing new versions with ever-increasing transmission rates. For example, we have seen an increase from 1.5 to 6 Gb/s between SATA 1 and SATA 3, from 2 to 970 Gb/s between PCIe 1.0x1 and PCIe 6.0x16, and from 0.0015 to 20 Gb/s between USB 1.0 and USB 3.2. The multitude of changes could lead to a nightmare for end users if the standards did not apply backward compatibility between consecutive versions.

For instance, a USB 2.0 device can be attached to a USB 3.0 port; conversely, a USB 3.0 device can be plugged into a USB 2.0 port. In both cases, the protocol will agree on the older of the two versions (in these examples, USB 2.0), resulting in communication with correspondingly lower efficiency. Importantly, the connection will still work. Analogous compatibility is generally observed between PCIe versions, as well as between SATA versions. There are some exceptions, such as SATA 2 and SATA 3 not being fully compatible with SATA 1, though the latter is now rarely used.

Simultaneously, the corresponding standards for connectors have also evolved, generally decreasing in size and introducing necessary adjustments for cooperating with newer bus standards. For example, the broadly known USB-A ports were soon accompanied by micro USB (or more precisely, USB micro-B) plugs, which, due to their smaller size, became widespread in mobile devices. Later, USB-C was introduced, featuring a symmetrical and more convenient plug shape, along with additional pins that allow larger throughput for both data and power.

![Figure 4. Evolution of connectors for the USB buses.](http://en.wikipedia.org)

Lastly, it is worth mentioning that the evolution of connectors has also increased compatibility between different bus standards. Initially, SATA and PCIe were simply terminated with SATA and PCIe ports, differing in both shape and size. Since 2013, however, the M.2 standard has specified the shape of the port (and the corresponding connector in a storage drive) together with a controller allowing communication according to any of the SATA, PCIe, or USB protocols, depending on the requirements of the connected device and potential limitations of the computer motherboard. However, while M.2 can fully support the SATA 3 protocol (allowing its top throughput of 6 Gb/s), it can handle only up to 4 transmission lanes in the case of PCIe. For a bus of x16 type, this means only 25% of the maximum bus throughput is achievable. Therefore, while M.2 drives can surpass the SATA barrier of efficiency from the end user's viewpoint, they still lag behind drives with the full PCIe interface.

### Logical Organization of Data

From a physical viewpoint, the memory cells form just a sequence of bits (0 and 1 values). However, in the case of storage drives, we want to store and then correctly interpret not just the data itself, but also the structure of files and folders containing them, the metadata of these objects, and additional data structures of the operating system. This necessitates an appropriate format for storing information on the drive.

### File Systems

Organizing data on a storage drive (e.g., choosing the location for saving new data or encoding the relationships between files and folders) is the responsibility of the operating system, which follows a specific set of rules called a file system.

For example, for HDD drives, the Windows and Linux systems employ by default the NTFS and ext4 file systems, respectively. Until a few years ago, this meant that an HDD formatted (with default settings) and modified under Linux was non-readable under Windows. Fortunately, the newest versions of Windows have introduced support for ext4, while Linux has long supported NTFS, at least in read-only mode.

A disadvantage of NTFS is the relatively high fragmentation of data. This means that logically related data (e.g., from a single file) can be placed in distant locations on the disk. As we have mentioned, this is suboptimal as it increases the total time spent accessing a file. To address this problem, Windows offers a procedure called defragmenting (also called optimizing or defragging), which restores some order to the stored data. In older versions of Windows, this procedure could only be triggered manually because of how engaging it was for overall PC efficiency. Newer versions introduced an option for automatic defragmenting, although the process can still be cumbersome.

For SSD drives, one can either use one of the leading file systems mentioned above or choose among new file systems dedicated to SSD drives. Examples include exFAT in Windows or F2FS in Linux.

#### Partitions

Partitions are explicit sections of the drive storage space that, from the viewpoint of the operating system and all running programs, act as fully independent storage units, just as if they were physically separate drives. For example, when on Windows we see several "drives" (C:, D:, E:, etc.), these may be subsequent partitions of a single physical drive, just acting as different logical drives. Each partition can be accessed with a different file system.

If a partition hosts an operating system, its initial sectors are reserved for the boot loader (as described in the lecture "Motherboard"). Similarly, if the partition is formatted with the NTFS file system, then NTFS reserves its initial part for a file called the Master File Table (MFT), which contains metadata for every file (e.g., name, location on the drive, size, modification date, and attributes such as "read-only" or "hidden"). The MFT also contains a bitmap indicating free and occupied clusters on the drive. To avoid fragmentation of the MFT file, the file system reserves a larger area upfront (called the MFT zone) to avoid placing other files there. Additionally, to recover from corruption of the MFT content, the file system keeps a copy (called the MFT mirror) on the drive.

#### Encryption

File systems also offer an option for encryption, meaning the drive stores an encrypted version of the actual information. This ensures that an unauthorized person cannot view the file contents on the drive, even if they gain possession of the computer, unmount the drive, and plug it in elsewhere, or use an alternative operating system.

A disadvantage of encryption is a potential slowdown of computer operations. Additionally, encryption does not guarantee "full safety." For example, even if the file contents are encrypted, the structure and names of files and folders typically are not.

It is also possible to encrypt a drive at the hardware level using methods like the Trusted Platform Module (TPM), which started appearing in computers in the last decade. Each instance of TPM contains unique encryption and decryption keys, designed to prevent retrieval of these keys from the device, and prevent removing the TPM from the motherboard without destroying the hardware. Encrypting the whole drive with TPM can be done from the BIOS / UEFI level. In this case, the booting process involves decrypting the boot loader, requiring the user to provide a password and initiate storage decryption even before the main operating system starts up. To facilitate this, another operating system is introduced—a smaller one with substantially limited functionality focused on security. An example of such a system is BitLocker.

Generally, hardware-level encryption is typically faster and more secure than software solutions. However, it may prevent the user from accessing their data if the computer is somehow damaged.
 

# ROM and booting

As we know from the previous lectures, the role of RAM includes storing the code of the currently running program. However, at the time when a computer is powered on, RAM does not contain any useful data. The operating system, which also participates in memory management, isn’t yet active either. To make setting up all of this possible, the computer motherboard contains an additional memory die. Clearly, it must be non-volatile memory, i.e, one which does not lose data during power-off periods.

That memory is usually of the flash EEPROM type. The name EEPROM can be a bit confusing, as it stands for: electrically erasable programmable read-only memory. The read-only-memory (ROM) part is here for historical reasons. Indeed, several production technologies ago, an important spot in computer design was occupied by memory in which data could be stored only once, at manufacturing time. However, later enhancements enabled that memory to be edited (“programmed”) long after its creation (leading to PROM), then to be erased with UV light and programmed again (EPROM), up to the modern solutions in which such memory can be erased and programmed again without even taking it out of the computer.

The main content of the built-in non-volatile memory is firmware purposed to be executed as the first code after the computer is powered on. This plays the role of a “restricted operating system”, enabling the processor to communicate with input/output devices on the motherboard (e.g, keyboard, disk, graphics card) until the true (much more complex) operating system is started and takes these tasks on.

For a long time, that initial firmware was usually based on a program for the IBM PC computer called BIOS — and, despite later extensions and adjustments, used to be still generally described as BIOS (Basic Input/Output System). In fact, that name can be still found in use, e.g, the abovementioned ROM memory is still sometimes called the BIOS die. However, in the last years, due to technical limitations typical to BIOS, its role has been taken over by a new firmware standard called UEFI (Unified Extensible Firmware Interface), developed and promoted in cooperation between multiple leading companies (including Intel, AMD, Lenovo, Dell, HP, Microsoft, and Apple),

Before going into the differences between BIOS and UEFI, we will describe the basic principles of the startup procedure of a computer and its operating system, which look similarly in both standards.

## Booting

One of the main tasks of BIOS/UEFI is executing a boot loader, responsible for loading the operating system code into RAM, and then executing that code. In modern computers, this procedure often consists of multiple stages:

* A first-stage boot loader (BIOS/UEFI), instead of loading the operating system, loads another second-stage boot loader, which can be e.g,:

—    a boot loader for MS Windows (bootmgr), offering the user a choice between Windows versions (if there is more than one installed), as well as an option to run Windows in so-called safe mode (a restricted, and hence more stable, version of the system);

—    the GRUB boot loader, offering the user a choice between various UNIX-like operating systems (including Linux) and MS Windows — of course, if there is more than one such system installed.

Only then, the proper operating system is invoked.

The second-stage boot loader is initially placed in the secondary memory, in a well-specified location of the particular storage device (e.g. for a hard drive, it is its first sector). (A part of a first-stage boot loader’s work is to cheek all the computer storage drives for one that has such a boot sector). 

One can also boot from a pendrive, a CD/DVD disc, or even from another computer in the local network. (Earlier in the past, there were also other technologies in use, like floppy discs, or even punched tapes or cards). 

Notably, during an installation procedure for an operating system, the second-stage boot loader role is taken by the installer.

## The POST self-cheek

Before BIOS/UEFI can proceed to the boot loader, it executes the POST procedure, which is the basic cheek of the crucial computer components. In particular, the cheeks involve the processor and main memory. In ease any erorrs have been found, the appropriate message will be displayed on the screen — however, in ease this could be impossible (e.g, due to a screen failure), the problems are additionally communicated with sound beeps. The exact meaning of these signals depends on the BIOS/UEFI manufacturer. Below, we list the meanings of sound signals according to one of the popular conventions, AMI BIOS:

|     |     |     |
| --- | --- | --- |
| Signal | Error type | Comment |
| 1 long | no error | the POST test has finished with success |
| 1 short | DRAM refresh error | e.g. an error while handling an interrupt |
| 2 short | memory parity error | unexpected value of the checksum bit |
| 3 short | RAM error | within the initial 64kiB |
| 4 short | system clock error |     |
| 5 short | CPU error |     |
| 6 short | A20 gate error | the A20 gate controls CPU access to memory addresses above 16MiB; an error in it prevents CPU from switching between modes of operation |
| 7 short | CPU virtual mode error |     |
| 8 short | video memory error |     |
| 9 short | ROM checksum error | ROM content has been corrupted |
| 10 short | CMOS memory error | CMOS is a small memory for BIOS settings (which is non-volatile thanks to permanent power supply from the CMOS battery) |
| 11 short | L2 cache error |     |
| 1    long,<br><br>2    short | video subsystem error |     |
| 1 long, 3 short | RAM error | outside the initial 64kiB |
| 1 long, 8 short | display error |     |
|alternating  high/low | insufficient power | insufficient CPU voltage or fan rotation speed

Occasionally, it’s worth to check certain components even more thoroughly, which can be achieved with special diagnostic programs. Memory or hard drive can be tested from the operating system level; however, some tools (often these more thorough, e.g. memtest86 for RAM) need to be launched from the BIOS/UEFI level.

## Settings

After POST finishes, the user can enter the settings mode. To land there, one needs to press a proper key — usually Esc or one of the function keys (F8, F12 etc,). The proper key depends on the BIOS/UEFI version; an information regarding which one is proper is displayed for some time on the startup screen.

In the settings mode, the user can adjust e.g, the clock frequency for the CPU, RAM, or system buses, the voltage powering the motherboard slots, or the computer fan rotation speed. Changing these parameters may improve computer efficiency — however, one should keep in mind that this brings a risk of unstable operation, or even damaging the hardware. Fortunately, at least as long as no component has been damaged, the settings mode allows restoring the factory defaults.

In that mode, the user can also set the order in which storage drives are checked for the boot loader. This is practically necessary if the top priority is currently assigned to the hard drive, while we want to boot from a pendrive (theoretically, an alternative is to take the hard drive out of the computer, though in practice it’s clearly easier to change the settings). On the other hand, putting the hard drive on top of that list can save a few seconds of waiting during every normal computer startup. Similarly, some time can be saved by switching unnecessary devices — for example, when there is a non-connected slot on the motherboard. Another benefit from such settings change can be increasing security (e.g, by switching off all USB data transmission).

### I/O interface

The last functionality of BIOS/UEFI to be mentioned here is defiinig interrupt handlers - that is, defining a way for the CPU to communicate with the input/output devices. 

Until the 1990's, BIOS served as an intermediate layer between the operating system and I/O devices (which is reflected in its name). Currently, managing I/O devices is done inside the operating system; thanks to this, the user can attach a new device (and, if needed, install its software driver) without upgrading their BIOS/UEFI.

However, I/O management in BIOS/UEFI is still retained - e.g. to ensure backward compatibility (so that older programs can still execute), though most importantly to enable the abovementioned booting procedure during which BIOS/UEFI must load data from secondary storage without any help from the operating system (which is not yet running at that time).

### BIOS vs. UEFI

From the user's viewpoint, the most noticeable di?erence between the newer UEFI and the older BIOS is appearance: while BIOS displays everything in ASCII mode, with no mouse support, UEFI offers a graphical interface (and, generally, more convenient usage). 

UEFI also removes some problems and limitations present in BIOS regarding handling hard drives (e.g. total size limited to 2 TiB, the number of so-called _primary partitions_ limited to 4). However, the impact extends to other computer components. Also, some settings (e.g. Secure Boot) can on one hand improve security by making malware attacks significantly harder, but on the other hand may complicate or even prevent installing some operating systems.

UEFI also offers an operating mode compatible with the BIOS standard (_Compatibility Support Mode_ - CSM; earlier also _Legacy BIOS_). Enabling it is necessary in case of some older components incompatible with the UEFI standard. On the other hand, some modules (e.g. Intel chipsets) do not offer compatibility with the BIOS standard. Similarly, the MS Windows operating system starting from version 11 - requires the Secure Boot setting to support some of its functionalities, and that is only available in the UEFI mode, not in the BIOS compatibility modes.

### Upgrades

As previously mentioned, upgrading the BIOS/UEFI on a specific computer may be necessary—for example, after replacing a hardware component. There are several ways to save a new version, listed below from the most high-level to the most low-level approaches:

1. From the level of an already running operating system (provided that the OS supports this);

2. From a special file placed on a pendrive, during booting, using the UEFI user interface;

3. From a special file placed on a pendrive, by pressing an appropriate button on the computer case (provided that the motherboard and the computer case both support this);

4. Directly to the EEPROM die (after opening the computer case), by using a dedicated device.

The more high-level ways are generally safer (e.g. the operating system and UEFI make an initial check of the update file, so that we do not risk e.g. using a "neighbouring" file of a wrong format by a plain mistake). 

Still, such an update is potentially dangerous - it could make some I/O device inaccessible. 

If we're unlucky enough to pick a UEFI version incompatible with our motherboard, we may even lose way to turn the computer on; in such case, the only remaining ways to fix this are methods 3 and 4. 

The takeaway is that upgrading BIOS/UEFI without a direct reason is not recommended.
