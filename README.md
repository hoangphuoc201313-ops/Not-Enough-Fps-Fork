Not-Enough-FPS
A small mod that increases Minecraft's FPS limit limit to 1000 and allows all numeric options to accept a directly typed input.

Fork: Minecraft 1.21.1 (Fabric)
This is a port of Not Enough FPS to Minecraft 1.21.1 (Fabric), based on upstream release 1.21.11-1.0.2 by Thedustbuster.

Upstream: https://github.com/Thedustbustr/Not-Enough-FPS — licensed under GPL-3.0-only (see LICENSE and FORK_NOTICES.md).

Changes relative to upstream 1.21.11-1.0.2
OptionsMixin: IntRange#xmap uses the 2-argument overload (1.21.1 has no 3-argument variant) and the change callback targets Minecraft#getWindow()#setFramerateLimit(int) (1.21.1 has no FramerateLimitTracker).
SliderControlElementMixin: input handlers ported to the 1.21.1 GUI API (mouseClicked(DDI)Z, keyPressed(III)Z, mouseDragged(DDIDD)Z) — 1.21.11's KeyEvent/MouseButtonEvent do not exist on 1.21.1; digits are resolved from the GLFW key code.
commitTypedValue guards against an empty buffer before parsing (fix carried over from upstream 26.3).
Dependencies: Minecraft 1.21.1, Fabric Loader 0.18.3+, Fabric API 0.116.17+1.21.1, Sodium mc1.21.1-0.8.13+ (required).
Build
Requires JDK 21.
./gradlew build

Testing checklist
Vanilla "Max Framerate" slider goes 1..1001 in steps of 1; 1001 shows as "Unlimited".
FPS actually exceeds 260 with the limit raised.
Click a numeric Sodium slider, type digits, Enter commits, Esc cancels, Backspace edits, mouse drag cancels typing.
F3 overlay shows "Unlimited" only at the raised cutoff.
