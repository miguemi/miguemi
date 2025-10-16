import React from "react";
import { motion } from "framer-motion";

// Single-file React component using Tailwind + Framer Motion
// Shows your intro with animated tech badges: Inertia, Nix, React, PHP, Laravel, Tailwind, JavaScript
// Drop into any React app (e.g., Vite, Next.js). Tailwind + framer-motion required.

const techs = [
  { name: "Inertia.js", emoji: "🧭", color: "from-indigo-500 to-purple-500" },
  { name: "Nix", emoji: "❄️", color: "from-cyan-500 to-blue-600" },
  { name: "React", emoji: "⚛️", color: "from-sky-500 to-blue-700" },
  { name: "PHP", emoji: "🐘", color: "from-violet-500 to-fuchsia-600" },
  { name: "Laravel", emoji: "🧱", color: "from-red-500 to-rose-600" },
  { name: "Tailwind", emoji: "🌀", color: "from-teal-400 to-emerald-500" },
  { name: "JavaScript", emoji: "🟨", color: "from-amber-400 to-yellow-500" },
];

const floatVariants = {
  initial: { y: 0 },
  animate: (i: number) => ({
    y: [0, -8, 0],
    transition: { duration: 2 + (i % 3) * 0.3, repeat: Infinity, ease: "easeInOut" },
  }),
};

const pop = {
  initial: { opacity: 0, scale: 0.9, y: 10 },
  animate: { opacity: 1, scale: 1, y: 0, transition: { duration: 0.4 } },
};

export default function MiguemiIntro() {
  return (
    <div className="min-h-screen w-full bg-gradient-to-b from-slate-950 via-slate-900 to-slate-950 text-white flex items-center justify-center p-6">
      {/* Subtle animated grid background */}
      <div className="absolute inset-0 -z-10 opacity-20 [background:radial-gradient(circle_at_center,theme(colors.slate.700)_1px,transparent_1px)] [background-size:20px_20px] animate-[pulse_6s_ease-in-out_infinite]" />

      <motion.main
        initial={{ opacity: 0, y: 20 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 0.5 }}
        className="w-full max-w-4xl"
      >
        {/* Header / Greeting */}
        <motion.section
          variants={pop}
          initial="initial"
          animate="animate"
          className="relative overflow-hidden rounded-3xl border border-slate-800 bg-slate-900/60 shadow-2xl"
        >
          <div className="px-8 py-10 md:px-12 md:py-14">
            <div className="flex items-center justify-center gap-4 text-5xl md:text-6xl">
              <motion.span
                animate={{ rotate: [0, -10, 10, 0] }}
                transition={{ duration: 1.8, repeat: Infinity, ease: "easeInOut" }}
                role="img"
                aria-label="tiger"
              >
                🐅
              </motion.span>
              <h1 className="font-black tracking-tight text-transparent bg-clip-text bg-gradient-to-r from-white to-slate-300">
                Hello!
              </h1>
            </div>

            <p className="mt-6 text-center text-lg md:text-xl text-slate-300">
              It's a pleasure to meet you! I'm <span className="font-semibold text-white">Miguemi</span>, and I'm a programmer!
            </p>

            {/* Centered emoji row like your original snippet */}
            <div className="mt-6 flex items-center justify-center gap-6 text-3xl md:text-4xl">
              <span title="Tiger">🐅</span>
              <span title="PHP">🐘</span>
              <span title="NixOS">❄️</span>
            </div>

            {/* Animated tech stack badges */}
            <div className="mt-10 grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-4">
              {techs.map((t, i) => (
                <motion.div
                  key={t.name}
                  custom={i}
                  variants={floatVariants}
                  initial="initial"
                  animate="animate"
                  whileHover={{ scale: 1.05 }}
                  className={`relative rounded-2xl p-[2px] bg-gradient-to-r ${t.color} shadow-lg`}
                >
                  <div className="rounded-2xl bg-slate-950/80 backdrop-blur px-4 py-3 flex items-center gap-3">
                    <span className="text-2xl" aria-hidden>{t.emoji}</span>
                    <span className="font-medium">{t.name}</span>
                  </div>
                </motion.div>
              ))}
            </div>

            {/* CTA / Links placeholder */}
            <div className="mt-10 flex flex-wrap items-center justify-center gap-3">
              <motion.a
                whileHover={{ y: -2 }}
                whileTap={{ scale: 0.98 }}
                href="#"
                className="rounded-2xl px-5 py-3 text-sm font-semibold bg-white text-slate-900 hover:bg-slate-100 shadow"
              >
                View Projects
              </motion.a>
              <motion.a
                whileHover={{ y: -2 }}
                whileTap={{ scale: 0.98 }}
                href="#"
                className="rounded-2xl px-5 py-3 text-sm font-semibold border border-slate-700 hover:border-slate-600 text-slate-200"
              >
                Contact Me
              </motion.a>
            </div>
          </div>

          {/* Decorative orbs */}
          <motion.div
            aria-hidden
            className="pointer-events-none absolute -top-20 -left-20 h-56 w-56 rounded-full bg-sky-500/20 blur-3xl"
            animate={{ x: [0, 10, 0], y: [0, -10, 0] }}
            transition={{ duration: 6, repeat: Infinity, ease: "easeInOut" }}
          />
          <motion.div
            aria-hidden
            className="pointer-events-none absolute -bottom-24 -right-16 h-64 w-64 rounded-full bg-fuchsia-500/10 blur-3xl"
            animate={{ x: [0, -10, 0], y: [0, 10, 0] }}
            transition={{ duration: 7, repeat: Infinity, ease: "easeInOut" }}
          />
        </motion.section>

        {/* Footer note */}
        <p className="mt-6 text-center text-sm text-slate-400">
          Built with React, Tailwind, and Framer Motion. Add Inertia.js/Laravel/PHP on the backend, and Nix for reproducible dev envs.
        </p>
      </motion.main>
    </div>
  );
}
