# Test5.Motherboard.NonVolatileStorage.ROMandBooting

# Test 5. Motherboard. Non-volatile Storage. ROM and booting

## Motherboard

The computer parts discussed so far — CPU, RAM dies, the BIOS die — are physically located on the motherboard. It is, as the name suggests, the place for attaching the most important components. Besides just hosting them, it enables them to communicate with each other.

On a modern motherboard, we will find e.g, those elements:
* a CPU slot (or socket) — a place to put a CPU in (though it also happens that the CPU is soldered directly to the
motherboard);

* RAM slots: typically DDR3, DDR4, DDR5 (here, it may also happen that memory is soldered directly to the motherboard1);

* the chipset (which will be discussed below);

* the BIOS die;

* the system clock generator, allowing synchronization between various components;

* power sockets, through which all the computer components arempowered with electricity;

* hard drive slots;

* optical drive (CD/DVD) slots;

* keyboard slots;
  
* extension card slots

(it is through them that we can connect a graphics card or a network card, or a USB port controller).

In practice, a motherboard can look as follows:

Figure 1. A Dell Precision T3600 motherboard (from year 2012).
(Source: http://en.wikipedia.org)

1 This happens e.g. for the LPDDR memory, which is used mainly in mobile devices (phones, tablets), though also in certain laptops. This memory kind is slower and more expensive than typical DDR but in reward it requires lower voltage, which allows longer operation on battery power.

Such organization of the board with standardized sockets/slots allows for some elasticity in choosing the components to be placed inside or attached to the computer. Unfortunately, even if a component can be attached physically, it/s still not guaranteed that it will be supported correctly by the motherboard and the processor. Hence, it/s essential to verify compatibility specifications on every hardware upgrade.

## Chipset

A **chipset** is literally “a set of (co-operating) integrated circuits". In the case of the motherboard chipset, we can distinguish (or rather “used to distinguish", though the recent changes will be discussed later) two such circuits, called the **northbridge** and the **southbridge**. These are the chips implementing the connection between the processor and the I/O devices. A scheme of the two-bridge architecture looks as follows:


Figure 2. A motherboard chipset with the two-bridge architecture.

As we see, the northbridge is located physically closer to the CPU. This is important, as it connects the components requiring the quickest access to the memory. In the early motherboards with the two-bridge structure (e.g. in the CS8220 chipset, which introduced a component called “northbridge" in 1986), the northbridge used to also contain a memory controller connected to memory buses. In the more modern solutions, as we mentioned above, these have been integrated into the processor.

The southbridge is not connected to the processor directly, but via the northbridge. That one connects — directly or indirectly — the processor to all the other (slower) input/output circuits.

In the most modern solutions, the tasks served so far by the northbridge have been taken over by the processor. This looks as follows:



Figure 3. A motherboard chipset with the one-bridge architecture.

Even in such a basic description, we can see that various computer components can fall into different categories:

•	a separate integrated circuit,

•	integrated with the motherboard,

•	integrated with the processor.

This choice is not visible from the user viewpoint, as long as there is no need of replacing some parts. This means that a higher level of integration leads to a risk of more expensive servicing once some components broke, or of hardware replacement becoming more difficult. On the other hand, the advantage of a higher level of integration can be better efficiency.

Altogether, this means that also in the future we can expect more changes of computer architecture in terms of moving various components between the above categories (just as it happened to the northbridge, and somewhat earlier — at least roughly — to the RAM controller).

## Buses

