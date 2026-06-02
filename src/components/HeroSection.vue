<template>
    <section
        id="hero"
        class="min-h-screen bg-black flex items-center pt-12 relative overflow-hidden"
    >
        <!-- Decorative Element -->
        <div
            class="text-9xl text-zinc-900 select-none pointer-events-none absolute top-20 right-10 font-mono"
        >
            {
        </div>

        <div
            class="max-w-7xl mx-auto px-6 grid grid-cols-1 lg:grid-cols-2 gap-16 items-center w-full"
        >
            <!-- Left Column -->
            <div class="z-10 flex flex-col items-center lg:items-start">
                <div
                    class="font-mono text-xs text-pink-500 uppercase tracking-widest border border-pink-900 px-4 py-2 mb-8"
                >
                    👾 AVAILABLE FOR FREELANCE WORK
                </div>

                <img
                    :src="data.profile.profileImage"
                    alt="Michele Domenico Vernone"
                    class="w-32 h-32 rounded-full border border-zinc-800 mb-8 object-cover"
                />

                <h1
                    class="font-mono text-6xl lg:text-8xl font-black leading-none"
                >
                    <span class="text-white">MICHELE</span>
                    <br />
                    <span class="text-white">DOMENICO</span>
                    <br />
                    <span class="text-pink-500">VERNONE</span>
                </h1>

                <p
                    class="font-mono text-zinc-400 text-sm mt-6 max-w-sm leading-relaxed"
                >
                    Game Developer. Building immersive worlds with C++, C#, UE5,
                    Godot, and whatever it takes.
                </p>

                <div class="font-mono text-xs text-zinc-600 mt-3">
                    // Bari, Italy
                </div>

                <div class="flex gap-4 mt-10">
                    <a
                        href="#projects"
                        class="border border-pink-500 text-pink-500 font-mono text-xs uppercase tracking-widest px-6 py-3 hover:bg-pink-500 hover:text-black transition-all duration-200"
                    >
                        VIEW PROJECTS
                    </a>
                    <a
                        href="#contact"
                        class="border border-zinc-700 text-zinc-400 font-mono text-xs uppercase tracking-widest px-6 py-3 hover:border-purple-500 hover:text-purple-400 transition-all duration-200"
                    >
                        CONTACT
                    </a>
                </div>
            </div>

            <!-- Right Column: HUD Panel -->
            <div class="z-10">
                <div class="border border-zinc-800 bg-zinc-950 p-6">
                    <div class="grid grid-cols-2 gap-4">
                        <!-- Engine -->
                        <div class="border-r border-b border-zinc-800 p-4">
                            <div
                                class="font-mono text-xs text-zinc-600 uppercase tracking-widest"
                            >
                                ENGINE
                            </div>
                            <div class="font-mono text-sm text-white mt-1">
                                UE5 / Godot / Unity
                            </div>
                        </div>
                        <!-- Lang -->
                        <div class="border-b border-zinc-800 p-4">
                            <div
                                class="font-mono text-xs text-zinc-600 uppercase tracking-widest"
                            >
                                LANG
                            </div>
                            <div class="font-mono text-sm text-white mt-1">
                                C++ / C# / GDScript
                            </div>
                        </div>
                        <!-- Location -->
                        <div class="border-r p-4">
                            <div
                                class="font-mono text-xs text-zinc-600 uppercase tracking-widest"
                            >
                                LOCATION
                            </div>
                            <div class="font-mono text-sm text-white mt-1">
                                Bari, Italy
                            </div>
                        </div>
                        <!-- Status -->
                        <div class="p-4">
                            <div
                                class="font-mono text-xs text-zinc-600 uppercase tracking-widest"
                            >
                                STATUS
                            </div>
                            <div class="font-mono text-sm text-pink-400 mt-1">
                                AVAILABLE
                            </div>
                        </div>
                        <!-- Projects -->
                        <div class="border-r p-4">
                            <div
                                class="font-mono text-xs text-zinc-600 uppercase tracking-widest"
                            >
                                PROJECTS
                            </div>
                            <div class="font-mono text-sm text-white mt-1">
                                4
                            </div>
                        </div>
                        <!-- Experience -->
                        <div class="p-4">
                            <div
                                class="font-mono text-xs text-zinc-600 uppercase tracking-widest"
                            >
                                LEVEL
                            </div>
                            <div class="font-mono text-sm text-purple-400 mt-1">
                                JUNIOR
                            </div>
                        </div>
                    </div>
                    <!-- Bottom strip -->
                    <div
                        class="h-px w-full bg-gradient-to-r from-pink-500 via-purple-500 to-transparent mt-2"
                    ></div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import data from "../data/portfolioData";
</script>
