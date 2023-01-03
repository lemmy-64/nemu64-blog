# Revisiting Nemu64

In September of 2020 I got interested in emulation again. It had been almost 20 years since I made my last contribution, and plenty of things had changed:

* Modern N64 emulators play essentially any game.
* HLE (mapping graphics to modern APIs like OpenGL) had essentially been perfected.
* LLE (accurately emulating the original console in a pixel perfect fashion) had essentially been perfected.
* Computers are a lot faster.

Well, that didn't stop me from seeing how far I'd get by modernizing a 20 year old codebase. Even if N64 emulation is a solved problem I could still have some fun in modernizing the Nemu of old?

However, the deeper I dug, the more it turned out that the above assumptions are not correct. While there has been huge progress over the last 20 years in making old games work, I realized there is still a huge opening for an emulator that provides:

* A really really accurate emulation core.
* That is heavily unit tested to provide consistent results.
* An emulator that is fast.
* An emulator that provides a great debugging experience.

There are a couple of motivations for me:
 * The N64 has seen a huge increase in interest of homebrew developers due to amazing projects like libdragon. As a result it is not enough to merely emulate behavior that old games happen to use, but instead the emulator should behave as much as the console as possible.
 * An emulator with a good debugger is a great learning experience for people to learn about how computers work. I myself learned assembly programming through watching an emulator that preceeded Nemu: Project Unreality. I want to be able to give the same to others.
 * Building an emulator that is both accurate and fast is the ultimate puzzle experience.

So that's what I set out to turn the Nemu of old into. Spoiler alert: I am not at that point yet, so I am not at a point where I feel ready to ship it yet. However, plenty of the work has happened and along the way I came up with some techniques that I wanted to share here.

The work to modernize Nemu64 involved/involves:
* Write a (huge) [unit testing suite that deeply tests the console or the emulator](02-test-everything.md).
* Write modern JITs that target x64 and aarch64.
* Write a modern JIT for the RSP, taking advantage of AVX2 and Neon.
* Revisit how caches work. Get timing right.
* Port to macOS and Linux.
* Integrate with ParallelRDP for LLE.
* For HLE, implement some new tricks like frame interpolation.
* Bring the old Debugger (which was written in Delphi) into the modern world.
* And plenty more

I am planning on writing about some of the topics above and will link them here.
