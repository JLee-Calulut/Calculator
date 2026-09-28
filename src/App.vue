<script setup>
import { ref } from 'vue';
import { useScrollReveal } from '@/Composables/useScrollReveal';
import AppIcon from '@/Components/UI/AppIcon.vue';
import Calculator from '@/Components/Calculator/Calculator.vue';
import HistoryPanel from '@/Components/Calculator/HistoryPanel.vue';
import useCalculator from '@/Composables/useCalculator';

// A single shared calculator instance powers both the keys and the panel.
const calc = useCalculator();

const main = ref(null);
useScrollReveal(main);
</script>

<template>
    <div class="min-h-screen bg-ink text-white">
        <section class="relative overflow-hidden">
            <!-- Dot-grid + glow backdrop, same treatment as the portfolio hero -->
            <div class="bg-grid absolute inset-0 opacity-60" aria-hidden="true" />
            <div class="absolute -top-24 right-1/4 h-80 w-80 rounded-full bg-orange-500/10 blur-3xl" aria-hidden="true" />

            <main ref="main" class="relative mx-auto max-w-6xl px-6 py-16 lg:py-24">
                <!-- Page heading -->
                <div class="reveal max-w-2xl">
                    <div class="flex items-center gap-3">
                        <span class="flex h-10 w-10 items-center justify-center rounded-xl border border-orange-500/30 bg-orange-500/10 text-orange-500">
                            <AppIcon name="terminal" class="h-5 w-5" />
                        </span>
                        <p class="font-mono text-sm text-orange-400">Personal project</p>
                    </div>
                    <h1 class="mt-4 text-3xl font-bold tracking-tight text-white sm:text-4xl">Calculator</h1>
                    <p class="mt-4 leading-relaxed text-neutral-400">
                        A keyboard-friendly daily calculator built with Vue 3 and Tailwind CSS —
                        chained operations, a rolling history, and floating-point-safe arithmetic.
                        Type with your keyboard or tap the keys below.
                    </p>
                </div>

                <!-- Calculator + history -->
                <div class="mt-12 grid items-start gap-8 lg:grid-cols-[minmax(0,24rem)_1fr]">
                    <div class="reveal w-full max-w-md rounded-3xl border border-ink-border bg-ink-soft/80 p-5 shadow-glow backdrop-blur">
                        <Calculator />
                    </div>

                    <aside class="reveal w-full max-w-md lg:max-w-none lg:pl-2">
                        <HistoryPanel
                            :history="calc.history.value"
                            @reuse="calc.reuseHistory"
                            @clear="calc.clearHistory"
                        />
                    </aside>
                </div>

                <footer class="mt-16 border-t border-ink-border pt-8 text-center text-xs text-neutral-600">
                    <p>
                        © <span class="font-mono">{{ new Date().getFullYear() }}</span> John Lee Calulut · Built with
                        <span class="text-orange-500/80">Vue 3</span> &amp;
                        <span class="text-orange-500/80">Tailwind CSS</span>
                    </p>
                </footer>
            </main>
        </section>
    </div>
</template>
