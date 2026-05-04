import { useState, useEffect, useMemo, useRef } from "react";
import {
  LayoutDashboard, Users, Search as SearchIcon, Mail, Briefcase, UserCheck,
  ListChecks, Wallet, FileText, Settings as SettingsIcon, Plus, X, Filter,
  ChevronDown, Edit3, Trash2, Copy, Check, Download, Upload, RotateCcw,
  ArrowUpRight, ArrowDownRight, Globe, Phone, Calendar, Flame, Sparkles,
  CircleDot, AlertCircle, ChevronRight, MoreHorizontal, ExternalLink,
  TrendingUp, Clock, Eye, Zap, Building2, CreditCard, BadgeCheck
} from "lucide-react";
import {
  BarChart, Bar, XAxis, YAxis, CartesianGrid, Tooltip, ResponsiveContainer,
  Cell, AreaChart, Area
} from "recharts";

/* ─────────────────────────── STORAGE ABSTRACTION ─────────────────────────── */
/* Single-key persistence. Swap implementation for localStorage / API later.   */
const STORAGE_KEY = "waas-app-state-v1";
const db = {
  async load() {
    try {
      const r = await window.storage.get(STORAGE_KEY);
      return r ? JSON.parse(r.value) : null;
    } catch { return null; }
  },
  async save(state) {
    try { await window.storage.set(STORAGE_KEY, JSON.stringify(state)); } catch {}
  },
  async clear() {
    try { await window.storage.delete(STORAGE_KEY); } catch {}
  }
};

/* ─────────────────────────── CONSTANTS / DOMAIN ──────────────────────────── */
const LEAD_STATUSES = [
  { id: "new", label: "Nový lead", tone: "stone" },
  { id: "audit", label: "Zkontrolovat web", tone: "amber" },
  { id: "ready", label: "Připraveno k oslovení", tone: "blue" },
  { id: "outreached", label: "Osloveno", tone: "indigo" },
  { id: "fu1", label: "Follow-up 1", tone: "violet" },
  { id: "fu2", label: "Follow-up 2", tone: "violet" },
  { id: "replied", label: "Odpověděl", tone: "emerald" },
  { id: "call", label: "Domluvený call", tone: "emerald" },
  { id: "offer", label: "Nabídka odeslána", tone: "amber" },
  { id: "won", label: "Vyhrané", tone: "emerald-deep" },
  { id: "lost", label: "Ztracené", tone: "stone" },
  { id: "dnc", label: "Neoslovovat", tone: "red" },
];

const DEAL_STATUSES = [
  { id: "new", label: "Nová příležitost", tone: "stone" },
  { id: "discovery", label: "Discovery call", tone: "blue" },
  { id: "proposal", label: "Poslán návrh", tone: "indigo" },
  { id: "waiting", label: "Čeká na rozhodnutí", tone: "amber" },
  { id: "negotiation", label: "Vyjednávání", tone: "violet" },
  { id: "won", label: "Vyhráno", tone: "emerald-deep" },
  { id: "lost", label: "Prohráno", tone: "stone" },
];

const TASK_STATUSES = [
  { id: "backlog", label: "Backlog", tone: "stone" },
  { id: "today", label: "Dnes", tone: "amber" },
  { id: "doing", label: "Probíhá", tone: "blue" },
  { id: "waiting", label: "Čeká na klienta", tone: "violet" },
  { id: "done", label: "Hotovo", tone: "emerald" },
];

const WEBSITE_STATES = ["Návrh", "Vývoj", "Revize", "Spuštěno", "Údržba", "Pozastaveno"];
const PAYMENT_STATES = ["Zaplaceno", "Čeká na platbu", "Po splatnosti", "Zrušeno"];
const PACKAGES = ["Basic", "Standard", "Premium", "Custom"];
const PRIORITIES = [
  { id: "low", label: "Nízká", color: "#a8a29e" },
  { id: "med", label: "Střední", color: "#d97706" },
  { id: "high", label: "Vysoká", color: "#b91c1c" },
];
const PAYMENT_TYPES = ["Měsíční předplatné", "Setup fee", "Doplňková práce", "Hosting", "Údržba"];

const PROJECT_CHECKLIST = [
  "Získat podklady od klienta",
  "Vytvořit strukturu webu",
  "Napsat texty",
  "Vytvořit design",
  "Vytvořit homepage",
  "Vytvořit podstránky",
  "Mobilní optimalizace",
  "Základní SEO",
  "Napojit kontaktní formulář",
  "Připojit doménu",
  "Finální kontrola",
  "Publikace",
  "Předání klientovi",
];

const TONE_STYLES = {
  stone:        { bg: "bg-stone-100",   text: "text-stone-700",   dot: "bg-stone-400",  ring: "ring-stone-200" },
  amber:        { bg: "bg-amber-50",    text: "text-amber-800",   dot: "bg-amber-500",  ring: "ring-amber-200" },
  blue:         { bg: "bg-blue-50",     text: "text-blue-800",    dot: "bg-blue-500",   ring: "ring-blue-200" },
  indigo:       { bg: "bg-indigo-50",   text: "text-indigo-800",  dot: "bg-indigo-500", ring: "ring-indigo-200" },
  violet:       { bg: "bg-violet-50",   text: "text-violet-800",  dot: "bg-violet-500", ring: "ring-violet-200" },
  emerald:      { bg: "bg-emerald-50",  text: "text-emerald-800", dot: "bg-emerald-500",ring: "ring-emerald-200" },
  "emerald-deep":{bg: "bg-emerald-100", text: "text-emerald-900", dot: "bg-emerald-700",ring: "ring-emerald-300" },
  red:          { bg: "bg-red-50",      text: "text-red-800",     dot: "bg-red-500",    ring: "ring-red-200" },
};

/* ─────────────────────────────── DEMO DATA ──────────────────────────────── */
const uid = () => Math.random().toString(36).slice(2, 10);
const today = () => new Date().toISOString().slice(0, 10);
const addDays = (d, n) => { const x = new Date(d); x.setDate(x.getDate()+n); return x.toISOString().slice(0,10); };

const seedState = () => {
  const l1 = uid(), l2 = uid(), l3 = uid(), l4 = uid(), l5 = uid(), l6 = uid(), l7 = uid();
  const c1 = uid(), c2 = uid(), c3 = uid();
  const d1 = uid(), d2 = uid(), d3 = uid();
  return {
    leads: [
      { id: l1, company: "Truhlářství Novák", website: "truhlarstvi-novak.cz", industry: "Řemeslo", city: "Brno",
        contact: "Pavel Novák", email: "info@truhlarstvi-novak.cz", phone: "+420 603 112 233",
        status: "ready", priority: "high", lastContact: addDays(today(),-3), nextFollowup: addDays(today(),2),
        note: "Mají hezké portfolio fotek, ale web vypadá jak z roku 2008.", monthlyValue: 3500,
        currentSite: "https://truhlarstvi-novak.cz",
        siteRating: "Slabý mobilní zážitek, žádná galerie, kontakt schovaný.",
        improvement: "Moderní galerie projektů + jasné CTA na nezávaznou poptávku.",
        angle: "Konkurence v Brně už má profi weby, vy přicházíte o klienty kteří jdou googlit." },
      { id: l2, company: "Zubní ordinace Dr. Marek", website: "zubarmarek.cz", industry: "Zdravotnictví", city: "Praha",
        contact: "MDDr. Marek Hejda", email: "ordinace@zubarmarek.cz", phone: "+420 222 333 444",
        status: "outreached", priority: "high", lastContact: addDays(today(),-1), nextFollowup: addDays(today(),4),
        note: "Vyšší segment, mohou si dovolit Premium balíček.", monthlyValue: 5500,
        currentSite: "https://zubarmarek.cz",
        siteRating: "Texty působí jako z brožury z 90. let, žádná možnost online objednávky.",
        improvement: "Online rezervace, sekce o lékařích, fotky ordinace, FAQ.",
        angle: "Pacienti dnes hledají zubaře přes mobil. Aktuální web je nutí volat — to je friction." },
      { id: l3, company: "Bistro Zelená vidlička", website: "zelenavidlicka.cz", industry: "Gastro", city: "Plzeň",
        contact: "Tereza Marešová", email: "ahoj@zelenavidlicka.cz", phone: "+420 777 888 999",
        status: "replied", priority: "med", lastContact: today(), nextFollowup: addDays(today(),1),
        note: "Odpověděla pozitivně, čeká na termín callu.", monthlyValue: 2900,
        currentSite: "https://zelenavidlicka.cz",
        siteRating: "Žádné menu online, jen FB odkaz.",
        improvement: "Týdenní menu, online rezervace stolu, fotogalerie jídel.",
        angle: "Lidé hledají menu před návštěvou. Bez něj odejdou ke konkurenci." },
      { id: l4, company: "Autoservis Beneš", website: "autobenes.cz", industry: "Auto", city: "Olomouc",
        contact: "Roman Beneš", email: "servis@autobenes.cz", phone: "+420 605 444 222",
        status: "fu1", priority: "med", lastContact: addDays(today(),-5), nextFollowup: today(),
        note: "První oslovení bez odpovědi, čas na follow-up.", monthlyValue: 3200,
        currentSite: "https://autobenes.cz",
        siteRating: "Statický web, nedá se objednat termín, špatně čitelný na mobilu.",
        improvement: "Online objednávka termínu, ceník, sekce hotových oprav.",
        angle: "Servisy v okolí už mají online rezervaci. Telefon dnes lidem vadí." },
      { id: l5, company: "Realitní kancelář Domov", website: "rkdomov.cz", industry: "Reality", city: "Praha",
        contact: "Lucie Pokorná", email: "info@rkdomov.cz", phone: "+420 731 222 111",
        status: "new", priority: "low", lastContact: "", nextFollowup: addDays(today(),3),
        note: "", monthlyValue: 4500, currentSite: "https://rkdomov.cz",
        siteRating: "", improvement: "", angle: "" },
      { id: l6, company: "Studio Krása", website: "studiokrasa.cz", industry: "Krása", city: "Brno",
        contact: "Markéta Dvořáková", email: "rezervace@studiokrasa.cz", phone: "+420 776 333 444",
        status: "call", priority: "high", lastContact: addDays(today(),-2), nextFollowup: addDays(today(),0),
        note: "Call domluvený na zítra v 10:00.", monthlyValue: 3900,
        currentSite: "https://studiokrasa.cz",
        siteRating: "Velmi pomalý web, fotky neoptimalizované, kontakt jen telefonem.",
        improvement: "Rychlý moderní web, online rezervace přes Booksy nebo vlastní řešení.",
        angle: "Při natáčení videa weby konkurence načítaly za 1.2s, váš za 6.4s." },
      { id: l7, company: "Klempířství Horák", website: "klempirstvi-horak.cz", industry: "Řemeslo", city: "Hradec Králové",
        contact: "Tomáš Horák", email: "horak@klempirstvi-horak.cz", phone: "+420 602 555 666",
        status: "lost", priority: "low", lastContact: addDays(today(),-30), nextFollowup: "",
        note: "Řekl že má bratrance který mu dělá web zadarmo. Klasika.", monthlyValue: 2500,
        currentSite: "https://klempirstvi-horak.cz",
        siteRating: "Web nefunguje na mobilu, žádné kontakty na první stránce.",
        improvement: "Kompletní redesign s důrazem na lokální SEO.",
        angle: "" },
    ],
    deals: [
      { id: d1, leadId: l3, status: "discovery", monthly: 2900, setup: 9000, probability: 60,
        lastActivity: today(), nextStep: "Po callu poslat krátkou nabídku", note: "" },
      { id: d2, leadId: l6, status: "proposal", monthly: 3900, setup: 12000, probability: 75,
        lastActivity: addDays(today(),-1), nextStep: "Follow-up zítra", note: "Líbí se jim varianta Premium." },
      { id: d3, leadId: l2, status: "negotiation", monthly: 5500, setup: 15000, probability: 50,
        lastActivity: addDays(today(),-2), nextStep: "Vyřešit otázku exkluzivity", note: "Chtějí roční slevu 10%." },
    ],
    clients: [
      { id: c1, company: "Květinářství U Lípy", domain: "kvetinarstviulipy.cz", package: "Standard",
        monthly: 3500, setup: 9000, startDate: addDays(today(),-95), nextPayment: addDays(today(),5),
        paymentStatus: "Zaplaceno", siteStatus: "Údržba",
        notes: "Klient ráda komunikuje přes WhatsApp. Posílá fotky kytic.",
        accessNote: "Domain registrar: Subreg | Hosting: Wedos | Přístupy v 1Password",
        requests: ["Přidat valentýnskou kategorii", "Aktualizovat telefon v patičce"],
        history: [{ date: addDays(today(),-2), text: "Posláno upozornění na fakturu" }] },
      { id: c2, company: "Fitness Dynamo", domain: "fitness-dynamo.cz", package: "Premium",
        monthly: 5500, setup: 15000, startDate: addDays(today(),-180), nextPayment: addDays(today(),-3),
        paymentStatus: "Po splatnosti", siteStatus: "Spuštěno",
        notes: "Větší klient, 3 lokace. Občas pomalejší v platbách.",
        accessNote: "WP admin v 1Password | analytics: Plausible",
        requests: ["Doplnit harmonogram lekcí na duben", "Upravit cenu permanentky"],
        history: [{ date: addDays(today(),-5), text: "Faktura odeslána" }] },
      { id: c3, company: "Advokátka JUDr. Svobodová", domain: "advokatka-svobodova.cz", package: "Basic",
        monthly: 1900, setup: 7000, startDate: addDays(today(),-40), nextPayment: addDays(today(),20),
        paymentStatus: "Zaplaceno", siteStatus: "Spuštěno",
        notes: "Konzervativní klient, formální tón.", accessNote: "Vše v 1Password",
        requests: [], history: [{ date: addDays(today(),-30), text: "Web spuštěn" }] },
    ],
    audits: {
      [l1]: {
        firstImpression: "Web vypadá jako z roku 2008, na mobilu rozbitý.",
        heroIssue: "Žádná hero sekce, jen šedé pozadí a logo.",
        copyIssue: "Texty popisují historii firmy, ale neříkají co zákazník získá.",
        ctaIssue: "CTA je 'Kontakt' v menu, nic víc.",
        trustIssue: "Žádné reference, žádná čísla, žádná tvář majitele.",
        mobileIssue: "Layout se rozsype, písmo příliš malé.",
        speedIssue: "Načítání 4.8s, neoptimalizované obrázky.",
        missingRefs: "Ano — chybí.", missingOffer: "Není jasné co konkrétně dělají.",
        score: 3, redesign: "Moderní jednostránkový web s galerií projektů, formulářem poptávky a referencemi.",
        salesAngle: "Konkurence v Brně už má pěkné weby, vy přicházíte o poptávky.",
      },
    },
    tasks: [
      { id: uid(), title: "Připravit homepage Květinářství", clientId: c1, priority: "med",
        deadline: addDays(today(),3), status: "doing", note: "Verze s velkým hero obrázkem" },
      { id: uid(), title: "Mobilní optimalizace Fitness Dynamo", clientId: c2, priority: "high",
        deadline: addDays(today(),1), status: "today", note: "" },
      { id: uid(), title: "Reklamace platby Fitness Dynamo", clientId: c2, priority: "high",
        deadline: today(), status: "today", note: "Klient po splatnosti, poslat 2. připomínku" },
      { id: uid(), title: "Texty pro Advokátku — Sekce služby", clientId: c3, priority: "low",
        deadline: addDays(today(),7), status: "waiting", note: "Čekám na podklady od klientky" },
      { id: uid(), title: "Audit Realitní kancelář Domov", clientId: null, priority: "med",
        deadline: addDays(today(),2), status: "backlog", note: "" },
      { id: uid(), title: "Outreach batch — řemesla Brno", clientId: null, priority: "high",
        deadline: today(), status: "today", note: "20 firem, šablona V3" },
    ],
    payments: [
      { id: uid(), clientId: c1, amount: 3500, type: "Měsíční předplatné", dueDate: addDays(today(),5),
        status: "Čeká na platbu", note: "" },
      { id: uid(), clientId: c2, amount: 5500, type: "Měsíční předplatné", dueDate: addDays(today(),-3),
        status: "Po splatnosti", note: "Druhá upomínka odeslána" },
      { id: uid(), clientId: c3, amount: 1900, type: "Měsíční předplatné", dueDate: addDays(today(),20),
        status: "Čeká na platbu", note: "" },
      { id: uid(), clientId: c1, amount: 9000, type: "Setup fee", dueDate: addDays(today(),-90),
        status: "Zaplaceno", note: "" },
      { id: uid(), clientId: c2, amount: 2400, type: "Doplňková práce", dueDate: addDays(today(),-10),
        status: "Zaplaceno", note: "Úprava harmonogramu" },
    ],
    templates: [
      { id: uid(), name: "Cold e-mail — řemeslník", type: "cold",
        subject: "Krátká myšlenka k webu {{company}}",
        body: "Dobrý den {{contact}},\n\nkoukal jsem na {{website}} a všiml jsem si, že {{problem}}.\n\nMám pár nápadů, jak by to šlo zlepšit — konkrétně {{improvement}}.\n\nMělo by smysl o tom 10 minut popovídat?\n\n{{senderName}}" },
      { id: uid(), name: "Follow-up 1", type: "fu",
        subject: "Re: Krátká myšlenka k webu {{company}}",
        body: "Dobrý den {{contact}},\n\nposílám jen krátkou připomínku k mému e-mailu z minulého týdne.\n\nVím že je toho hodně — stačí mi věta jestli to dává smysl, nebo radši ne.\n\n{{senderName}}" },
      { id: uid(), name: "Follow-up 2 — break-up", type: "fu",
        subject: "Poslední pokus — {{company}}",
        body: "Dobrý den {{contact}},\n\nzkouším naposledy. Pokud teď není správný čas, napište mi prosím jen 'ne' a přestanu Vás otravovat.\n\nMějte se,\n{{senderName}}" },
    ],
    settings: {
      brand: "WAAS Studio",
      myName: "Vlastník",
      myEmail: "ja@waas.cz",
      currency: "Kč",
      defaultMonthly: 3500,
      defaultSetup: 9000,
      packages: [
        { name: "Basic", monthly: 1900, setup: 7000, includes: "1 stránka, kontaktní formulář, mobilní verze, hosting" },
        { name: "Standard", monthly: 3500, setup: 9000, includes: "Až 5 stránek, blog, SEO základ, hosting, údržba" },
        { name: "Premium", monthly: 5500, setup: 15000, includes: "Plně custom, neomezeně stránek, integrace, prioritní podpora" },
      ],
    },
  };
};

/* ───────────────────────────────── HELPERS ──────────────────────────────── */
const fmtMoney = (n, c = "Kč") => `${(n||0).toLocaleString("cs-CZ")} ${c}`;
const daysFromToday = (d) => {
  if (!d) return null;
  const diff = Math.round((new Date(d) - new Date(today())) / 86400000);
  return diff;
};
const statusMeta = (list, id) => list.find(s => s.id === id) || list[0];

/* ─────────────────────────── PRIMITIVES (UI) ────────────────────────────── */
function StatusPill({ list, id, onClick, editable }) {
  const meta = statusMeta(list, id);
  const t = TONE_STYLES[meta.tone] || TONE_STYLES.stone;
  return (
    <button
      type="button"
      onClick={onClick}
      disabled={!editable}
      className={`inline-flex items-center gap-1.5 px-2 py-0.5 rounded-md text-[11px] font-medium ring-1 ring-inset ${t.bg} ${t.text} ${t.ring} ${editable ? "hover:brightness-95 cursor-pointer" : "cursor-default"}`}
    >
      <span className={`w-1.5 h-1.5 rounded-full ${t.dot}`} />
      {meta.label}
    </button>
  );
}

function PriorityDot({ p }) {
  const meta = PRIORITIES.find(x => x.id === p) || PRIORITIES[0];
  return (
    <span className="inline-flex items-center gap-1.5 text-[11px] text-stone-600">
      <span className="w-2 h-2 rounded-full" style={{ background: meta.color }} />
      {meta.label}
    </span>
  );
}

function IconBtn({ icon: Icon, onClick, title, danger }) {
  return (
    <button onClick={onClick} title={title}
      className={`p-1.5 rounded-md hover:bg-stone-100 text-stone-500 ${danger ? "hover:text-red-700 hover:bg-red-50" : "hover:text-stone-900"}`}>
      <Icon size={14} />
    </button>
  );
}

function Btn({ children, onClick, variant = "primary", icon: Icon, type = "button", small, disabled }) {
  const base = "inline-flex items-center gap-1.5 font-medium transition-colors rounded-md disabled:opacity-50 disabled:cursor-not-allowed";
  const sizes = small ? "px-2.5 py-1 text-[12px]" : "px-3 py-1.5 text-[13px]";
  const variants = {
    primary: "bg-stone-900 text-stone-50 hover:bg-stone-800",
    secondary: "bg-white text-stone-800 ring-1 ring-stone-200 hover:bg-stone-50",
    ghost: "text-stone-600 hover:bg-stone-100 hover:text-stone-900",
    danger: "bg-white text-red-700 ring-1 ring-red-200 hover:bg-red-50",
    accent: "bg-amber-700 text-amber-50 hover:bg-amber-800",
  };
  return (
    <button type={type} onClick={onClick} disabled={disabled} className={`${base} ${sizes} ${variants[variant]}`}>
      {Icon && <Icon size={small ? 12 : 14} />} {children}
    </button>
  );
}

function Field({ label, children, hint, full }) {
  return (
    <label className={`flex flex-col gap-1 ${full ? "col-span-2" : ""}`}>
      <span className="text-[11px] uppercase tracking-wider text-stone-500 font-medium">{label}</span>
      {children}
      {hint && <span className="text-[11px] text-stone-400">{hint}</span>}
    </label>
  );
}

const inputCls = "w-full px-2.5 py-1.5 text-[13px] bg-white ring-1 ring-stone-200 rounded-md focus:ring-stone-400 focus:outline-none placeholder:text-stone-400";

function TextInput(props)    { return <input {...props} className={inputCls} />; }
function NumberInput(props)  { return <input type="number" {...props} className={inputCls} />; }
function DateInput(props)    { return <input type="date" {...props} className={inputCls} />; }
function TextArea(props)     { return <textarea rows={3} {...props} className={inputCls + " resize-y"} />; }
function Select({ options, ...props }) {
  return (
    <select {...props} className={inputCls + " appearance-none bg-no-repeat bg-right pr-7"}
      style={{ backgroundImage: "url(\"data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='12' height='12' fill='%23a8a29e' viewBox='0 0 16 16'><path d='M3.5 5.5l4.5 5 4.5-5z'/></svg>\")",
               backgroundPosition: "right 8px center" }}>
      {options.map(o => (
        <option key={typeof o === "string" ? o : o.id} value={typeof o === "string" ? o : o.id}>
          {typeof o === "string" ? o : o.label}
        </option>
      ))}
    </select>
  );
}

function Modal({ open, onClose, title, children, wide }) {
  if (!open) return null;
  return (
    <div className="fixed inset-0 z-50 flex items-center justify-center p-4 bg-stone-900/40 backdrop-blur-sm" onClick={onClose}>
      <div onClick={e => e.stopPropagation()}
        className={`bg-stone-50 rounded-xl shadow-2xl ring-1 ring-stone-200 w-full ${wide ? "max-w-4xl" : "max-w-xl"} max-h-[90vh] flex flex-col`}>
        <div className="flex items-center justify-between px-5 py-3 border-b border-stone-200">
          <h3 className="text-[15px] font-semibold text-stone-900">{title}</h3>
          <button onClick={onClose} className="p-1 rounded-md hover:bg-stone-200 text-stone-500"><X size={16} /></button>
        </div>
        <div className="overflow-y-auto px-5 py-4">{children}</div>
      </div>
    </div>
  );
}

function EmptyState({ icon: Icon, title, hint, action }) {
  return (
    <div className="flex flex-col items-center justify-center text-center py-16 px-8 rounded-xl border border-dashed border-stone-300 bg-stone-50/60">
      <div className="w-10 h-10 rounded-full bg-white ring-1 ring-stone-200 flex items-center justify-center mb-3 text-stone-500">
        <Icon size={18} />
      </div>
      <div className="text-[14px] font-medium text-stone-800">{title}</div>
      <div className="text-[12px] text-stone-500 mt-1 max-w-sm">{hint}</div>
      {action && <div className="mt-4">{action}</div>}
    </div>
  );
}

function Card({ children, className = "" }) {
  return <div className={`bg-white rounded-xl ring-1 ring-stone-200 ${className}`}>{children}</div>;
}

function Stat({ label, value, sub, trend, icon: Icon, accent }) {
  return (
    <Card className="p-4">
      <div className="flex items-start justify-between">
        <div className="text-[11px] uppercase tracking-wider text-stone-500 font-medium">{label}</div>
        {Icon && <div className={`p-1.5 rounded-md ${accent ? "bg-amber-50 text-amber-700" : "bg-stone-100 text-stone-500"}`}><Icon size={13} /></div>}
      </div>
      <div className="mt-2 text-[22px] font-semibold text-stone-900 tracking-tight tabular-nums">{value}</div>
      <div className="mt-1 flex items-center gap-1.5 text-[11px] text-stone-500">
        {trend === "up" && <ArrowUpRight size={12} className="text-emerald-700" />}
        {trend === "down" && <ArrowDownRight size={12} className="text-red-700" />}
        {sub}
      </div>
    </Card>
  );
}

/* ───────────────────────────── DASHBOARD PAGE ──────────────────────────── */
function DashboardPage({ state, onGoto }) {
  const { leads, clients, deals } = state;
  const m = useMemo(() => {
    const totalLeads = leads.length;
    const outreached = leads.filter(l => ["outreached","fu1","fu2","replied","call","offer","won","lost"].includes(l.status)).length;
    const replied = leads.filter(l => ["replied","call","offer","won"].includes(l.status)).length;
    const calls = leads.filter(l => ["call","offer","won"].includes(l.status)).length;
    const wonLeads = leads.filter(l => l.status === "won").length;
    const mrr = clients.filter(c => c.paymentStatus !== "Zrušeno").reduce((s,c) => s + (c.monthly||0), 0);
    const activeDeals = deals.filter(d => !["won","lost"].includes(d.status));
    const expectedFromDeals = activeDeals.reduce((s,d) => s + (d.monthly * (d.probability/100)), 0);
    const sitesInProduction = clients.filter(c => ["Návrh","Vývoj","Revize"].includes(c.siteStatus)).length;
    const overdue = clients.filter(c => c.paymentStatus === "Po splatnosti").length;
    const replyRate = outreached ? Math.round(replied/outreached*100) : 0;
    const closeRate = replied ? Math.round(wonLeads/replied*100) : 0;
    return { totalLeads, outreached, replied, calls, wonLeads, mrr, expectedFromDeals,
             sitesInProduction, overdue, replyRate, closeRate };
  }, [leads, clients, deals]);

  const pipelineData = useMemo(() => {
    return LEAD_STATUSES
      .filter(s => !["won","lost","dnc"].includes(s.id))
      .map(s => ({ name: s.label, value: leads.filter(l => l.status === s.id).length, tone: s.tone }));
  }, [leads]);

  const upcoming = useMemo(() => {
    return [...leads]
      .filter(l => l.nextFollowup && !["won","lost","dnc"].includes(l.status))
      .sort((a,b) => new Date(a.nextFollowup) - new Date(b.nextFollowup))
      .slice(0, 5);
  }, [leads]);

  return (
    <div className="space-y-6">
      <div>
        <h2 className="text-[20px] font-semibold text-stone-900 tracking-tight">Přehled</h2>
        <p className="text-[13px] text-stone-500 mt-0.5">Kde stojí tvůj WAAS business právě teď.</p>
      </div>

      <div className="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-3">
        <Stat label="MRR" value={fmtMoney(m.mrr)} sub={`${clients.filter(c=>c.paymentStatus!=='Zrušeno').length} platících klientů`} icon={Wallet} accent />
        <Stat label="Očekávaný příjem (deals)" value={fmtMoney(Math.round(m.expectedFromDeals))} sub="vážená pipeline hodnota" icon={TrendingUp} />
        <Stat label="Webů ve výrobě" value={m.sitesInProduction} sub="návrh / vývoj / revize" icon={Briefcase} />
        <Stat label="Po splatnosti" value={m.overdue} sub={m.overdue > 0 ? "vyřešit dnes" : "vše OK"} icon={AlertCircle} />
        <Stat label="Všechny leady" value={m.totalLeads} icon={Users} />
        <Stat label="Osloveno" value={m.outreached} sub={`${m.replyRate}% reply rate`} icon={Mail} trend="up" />
        <Stat label="Domluvené cally" value={m.calls} icon={Phone} />
        <Stat label="Klienti" value={clients.length} sub={`${m.closeRate}% close rate`} icon={UserCheck} />
      </div>

      <div className="grid grid-cols-1 lg:grid-cols-3 gap-4">
        <Card className="p-5 lg:col-span-2">
          <div className="flex items-center justify-between mb-4">
            <div>
              <h3 className="text-[14px] font-semibold text-stone-900">Pipeline podle stavu</h3>
              <p className="text-[12px] text-stone-500">Jak se leady rozkládají v aktuální pipeline</p>
            </div>
            <Btn variant="ghost" small onClick={() => onGoto("leads")}>Otevřít leady <ChevronRight size={12} /></Btn>
          </div>
          <div className="h-56">
            <ResponsiveContainer width="100%" height="100%">
              <BarChart data={pipelineData} margin={{ top: 5, right: 10, left: -20, bottom: 40 }}>
                <CartesianGrid strokeDasharray="3 3" stroke="#e7e5e4" />
                <XAxis dataKey="name" tick={{ fontSize: 10, fill: "#78716c" }} angle={-30} textAnchor="end" height={50} interval={0}/>
                <YAxis tick={{ fontSize: 10, fill: "#78716c" }} allowDecimals={false}/>
                <Tooltip cursor={{ fill: "#f5f5f4" }} contentStyle={{ fontSize: 12, borderRadius: 8, border: "1px solid #e7e5e4" }} />
                <Bar dataKey="value" radius={[4,4,0,0]}>
                  {pipelineData.map((d, i) => (
                    <Cell key={i} fill={
                      d.tone === "emerald" ? "#10b981" :
                      d.tone === "amber" ? "#d97706" :
                      d.tone === "blue" ? "#3b82f6" :
                      d.tone === "indigo" ? "#6366f1" :
                      d.tone === "violet" ? "#8b5cf6" : "#a8a29e"
                    } />
                  ))}
                </Bar>
              </BarChart>
            </ResponsiveContainer>
          </div>
        </Card>

        <Card className="p-5">
          <h3 className="text-[14px] font-semibold text-stone-900 mb-4">Co dělat dnes</h3>
          {upcoming.length === 0 ? (
            <div className="text-[12px] text-stone-500">Žádné nadcházející follow-upy. Přidej si první lead.</div>
          ) : (
            <div className="divide-y divide-stone-100">
              {upcoming.map(l => {
                const d = daysFromToday(l.nextFollowup);
                const overdue = d !== null && d < 0;
                return (
                  <div key={l.id} className="py-2.5 flex items-start gap-3">
                    <div className={`mt-0.5 w-1.5 h-1.5 rounded-full ${overdue ? "bg-red-500" : d === 0 ? "bg-amber-500" : "bg-stone-300"}`} />
                    <div className="flex-1 min-w-0">
                      <div className="text-[13px] font-medium text-stone-800 truncate">{l.company}</div>
                      <div className="text-[11px] text-stone-500 mt-0.5">
                        {overdue ? `${Math.abs(d)}d po termínu` : d === 0 ? "Dnes" : `Za ${d}d`} · <StatusPill list={LEAD_STATUSES} id={l.status} /></div>
                    </div>
                  </div>
                );
              })}
            </div>
          )}
        </Card>
      </div>
    </div>
  );
}

/* ─────────────────────────── LEAD MODAL / FORM ─────────────────────────── */
function LeadForm({ initial, onSave, onClose, onDelete }) {
  const [f, setF] = useState(initial || {
    id: uid(), company: "", website: "", industry: "", city: "", contact: "", email: "", phone: "",
    status: "new", priority: "med", lastContact: "", nextFollowup: "", note: "",
    monthlyValue: 3500, currentSite: "", siteRating: "", improvement: "", angle: "",
  });
  const set = (k,v) => setF(s => ({ ...s, [k]: v }));
  return (
    <div className="space-y-4">
      <div className="grid grid-cols-2 gap-3">
        <Field label="Název firmy"><TextInput value={f.company} onChange={e => set("company", e.target.value)} placeholder="Truhlářství Novák" /></Field>
        <Field label="Webová stránka"><TextInput value={f.website} onChange={e => set("website", e.target.value)} placeholder="firma.cz" /></Field>
        <Field label="Obor"><TextInput value={f.industry} onChange={e => set("industry", e.target.value)} placeholder="Řemeslo, gastro, …" /></Field>
        <Field label="Město / lokalita"><TextInput value={f.city} onChange={e => set("city", e.target.value)} /></Field>
        <Field label="Kontaktní osoba"><TextInput value={f.contact} onChange={e => set("contact", e.target.value)} /></Field>
        <Field label="E-mail"><TextInput value={f.email} onChange={e => set("email", e.target.value)} /></Field>
        <Field label="Telefon"><TextInput value={f.phone} onChange={e => set("phone", e.target.value)} /></Field>
        <Field label="Potenciální měsíční hodnota (Kč)">
          <NumberInput value={f.monthlyValue} onChange={e => set("monthlyValue", +e.target.value)} />
        </Field>
        <Field label="Stav"><Select value={f.status} onChange={e => set("status", e.target.value)} options={LEAD_STATUSES} /></Field>
        <Field label="Priorita"><Select value={f.priority} onChange={e => set("priority", e.target.value)} options={PRIORITIES} /></Field>
        <Field label="Datum posledního kontaktu"><DateInput value={f.lastContact} onChange={e => set("lastContact", e.target.value)} /></Field>
        <Field label="Datum dalšího follow-upu"><DateInput value={f.nextFollowup} onChange={e => set("nextFollowup", e.target.value)} /></Field>
        <Field label="Odkaz na současný web" full><TextInput value={f.currentSite} onChange={e => set("currentSite", e.target.value)} placeholder="https://..." /></Field>
        <Field label="Krátké hodnocení současného webu" full><TextArea value={f.siteRating} onChange={e => set("siteRating", e.target.value)} /></Field>
        <Field label="Navržené zlepšení" full><TextArea value={f.improvement} onChange={e => set("improvement", e.target.value)} /></Field>
        <Field label="Personalizovaný úhel oslovení" full><TextArea value={f.angle} onChange={e => set("angle", e.target.value)} /></Field>
        <Field label="Poznámka" full><TextArea value={f.note} onChange={e => set("note", e.target.value)} /></Field>
      </div>
      <div className="flex justify-between pt-2 border-t border-stone-200">
        <div>{onDelete && <Btn variant="danger" small onClick={() => { if (confirm("Smazat lead?")) onDelete(); }} icon={Trash2}>Smazat</Btn>}</div>
        <div className="flex gap-2">
          <Btn variant="secondary" onClick={onClose}>Zrušit</Btn>
          <Btn onClick={() => { onSave(f); onClose(); }}>Uložit</Btn>
        </div>
      </div>
    </div>
  );
}

/* ───────────────────────────── LEADS PAGE ──────────────────────────────── */
function LeadsPage({ state, setState, openLead }) {
  const [filterStatus, setFilterStatus] = useState("all");
  const [filterPriority, setFilterPriority] = useState("all");
  const [search, setSearch] = useState("");
  const [editing, setEditing] = useState(null);
  const [creating, setCreating] = useState(false);
  const [view, setView] = useState("table"); // table | kanban

  const filtered = useMemo(() => {
    return state.leads.filter(l => {
      if (filterStatus !== "all" && l.status !== filterStatus) return false;
      if (filterPriority !== "all" && l.priority !== filterPriority) return false;
      if (search && !l.company.toLowerCase().includes(search.toLowerCase())) return false;
      return true;
    });
  }, [state.leads, filterStatus, filterPriority, search]);

  const saveLead = (lead) => {
    setState(s => ({ ...s, leads: s.leads.some(l => l.id === lead.id) ? s.leads.map(l => l.id === lead.id ? lead : l) : [lead, ...s.leads] }));
  };
  const deleteLead = (id) => {
    setState(s => ({ ...s, leads: s.leads.filter(l => l.id !== id) }));
  };
  const cycleStatus = (id) => {
    setState(s => ({
      ...s,
      leads: s.leads.map(l => {
        if (l.id !== id) return l;
        const i = LEAD_STATUSES.findIndex(x => x.id === l.status);
        const next = LEAD_STATUSES[(i + 1) % LEAD_STATUSES.length];
        return { ...l, status: next.id };
      })
    }));
  };

  return (
    <div className="space-y-4">
      <div className="flex items-end justify-between flex-wrap gap-3">
        <div>
          <h2 className="text-[20px] font-semibold text-stone-900 tracking-tight">Lead Tracker</h2>
          <p className="text-[13px] text-stone-500 mt-0.5">{state.leads.length} leadů celkem · {filtered.length} zobrazeno</p>
        </div>
        <div className="flex items-center gap-2">
          <div className="flex bg-stone-100 rounded-md p-0.5">
            <button onClick={() => setView("table")} className={`px-2.5 py-1 text-[12px] rounded ${view === "table" ? "bg-white shadow-sm text-stone-900" : "text-stone-500"}`}>Tabulka</button>
            <button onClick={() => setView("kanban")} className={`px-2.5 py-1 text-[12px] rounded ${view === "kanban" ? "bg-white shadow-sm text-stone-900" : "text-stone-500"}`}>Kanban</button>
          </div>
          <Btn icon={Plus} onClick={() => setCreating(true)}>Přidat lead</Btn>
        </div>
      </div>

      <Card className="p-3 flex flex-wrap items-center gap-2">
        <div className="relative flex-1 min-w-[200px]">
          <SearchIcon size={14} className="absolute left-2.5 top-2.5 text-stone-400" />
          <input value={search} onChange={e => setSearch(e.target.value)} placeholder="Hledat firmu…"
            className="w-full pl-8 pr-3 py-1.5 text-[13px] bg-stone-50 ring-1 ring-stone-200 rounded-md focus:ring-stone-400 focus:outline-none" />
        </div>
        <Select value={filterStatus} onChange={e => setFilterStatus(e.target.value)}
          options={[{ id: "all", label: "Všechny stavy" }, ...LEAD_STATUSES]} />
        <Select value={filterPriority} onChange={e => setFilterPriority(e.target.value)}
          options={[{ id: "all", label: "Všechny priority" }, ...PRIORITIES]} />
      </Card>

      {filtered.length === 0 ? (
        <EmptyState icon={Users} title="Žádné leady" hint="Začni přidáním firmy, kterou chceš oslovit. Lead = příležitost. Konverze začíná tady."
          action={<Btn icon={Plus} onClick={() => setCreating(true)}>Přidat první lead</Btn>} />
      ) : view === "table" ? (
        <Card className="overflow-hidden">
          <div className="overflow-x-auto">
            <table className="w-full text-[13px]">
              <thead>
                <tr className="bg-stone-50 text-stone-500 text-[11px] uppercase tracking-wider">
                  <th className="text-left px-4 py-2.5 font-medium">Firma</th>
                  <th className="text-left px-4 py-2.5 font-medium">Stav</th>
                  <th className="text-left px-4 py-2.5 font-medium">Priorita</th>
                  <th className="text-left px-4 py-2.5 font-medium">Hodnota</th>
                  <th className="text-left px-4 py-2.5 font-medium">Další krok</th>
                  <th className="px-4 py-2.5"></th>
                </tr>
              </thead>
              <tbody className="divide-y divide-stone-100">
                {filtered.map(l => {
                  const d = daysFromToday(l.nextFollowup);
                  return (
                    <tr key={l.id} className="hover:bg-stone-50 cursor-pointer" onClick={() => openLead(l.id)}>
                      <td className="px-4 py-3">
                        <div className="font-medium text-stone-900">{l.company}</div>
                        <div className="text-[11px] text-stone-500 flex items-center gap-2 mt-0.5">
                          {l.industry && <span>{l.industry}</span>}
                          {l.city && <><span>·</span><span>{l.city}</span></>}
                          {l.website && <><span>·</span><a href={l.currentSite || `https://${l.website}`} target="_blank" rel="noreferrer"
                            onClick={e => e.stopPropagation()} className="text-stone-600 hover:text-stone-900 inline-flex items-center gap-1">
                            <Globe size={10} />{l.website}</a></>}
                        </div>
                      </td>
                      <td className="px-4 py-3" onClick={e => { e.stopPropagation(); cycleStatus(l.id); }}>
                        <StatusPill list={LEAD_STATUSES} id={l.status} editable />
                      </td>
                      <td className="px-4 py-3"><PriorityDot p={l.priority} /></td>
                      <td className="px-4 py-3 text-stone-700 tabular-nums">{fmtMoney(l.monthlyValue)}/měs</td>
                      <td className="px-4 py-3">
                        {l.nextFollowup ? (
                          <span className={`text-[12px] ${d < 0 ? "text-red-700" : d === 0 ? "text-amber-700" : "text-stone-600"}`}>
                            {d < 0 ? `${Math.abs(d)}d po termínu` : d === 0 ? "Dnes" : `Za ${d}d`}
                          </span>
                        ) : <span className="text-stone-400 text-[12px]">—</span>}
                      </td>
                      <td className="px-2 py-2 text-right" onClick={e => e.stopPropagation()}>
                        <IconBtn icon={Edit3} title="Upravit" onClick={() => setEditing(l)} />
                        <IconBtn icon={Trash2} title="Smazat" danger onClick={() => { if (confirm("Smazat?")) deleteLead(l.id); }} />
                      </td>
                    </tr>
                  );
                })}
              </tbody>
            </table>
          </div>
        </Card>
      ) : (
        <div className="overflow-x-auto pb-2">
          <div className="flex gap-3 min-w-max">
            {LEAD_STATUSES.map(s => {
              const items = filtered.filter(l => l.status === s.id);
              const t = TONE_STYLES[s.tone] || TONE_STYLES.stone;
              return (
                <div key={s.id} className="w-64 shrink-0">
                  <div className={`flex items-center justify-between mb-2 px-2 py-1 rounded-md ${t.bg}`}>
                    <div className={`text-[12px] font-medium ${t.text}`}>{s.label}</div>
                    <div className={`text-[11px] ${t.text} opacity-70`}>{items.length}</div>
                  </div>
                  <div className="space-y-2">
                    {items.map(l => (
                      <div key={l.id} onClick={() => openLead(l.id)}
                        className="bg-white rounded-md ring-1 ring-stone-200 p-3 cursor-pointer hover:ring-stone-300">
                        <div className="font-medium text-[13px] text-stone-900 truncate">{l.company}</div>
                        <div className="text-[11px] text-stone-500 mt-0.5">{l.industry} · {l.city}</div>
                        <div className="flex items-center justify-between mt-2">
                          <PriorityDot p={l.priority} />
                          <div className="text-[11px] text-stone-600 tabular-nums">{fmtMoney(l.monthlyValue)}</div>
                        </div>
                      </div>
                    ))}
                    {items.length === 0 && <div className="text-[11px] text-stone-400 text-center py-4 border border-dashed border-stone-200 rounded-md">Prázdné</div>}
                  </div>
                </div>
              );
            })}
          </div>
        </div>
      )}

      <Modal open={creating} onClose={() => setCreating(false)} title="Nový lead" wide>
        <LeadForm onSave={saveLead} onClose={() => setCreating(false)} />
      </Modal>
      <Modal open={!!editing} onClose={() => setEditing(null)} title="Upravit lead" wide>
        {editing && <LeadForm initial={editing} onSave={saveLead} onClose={() => setEditing(null)} onDelete={() => { deleteLead(editing.id); setEditing(null); }} />}
      </Modal>
    </div>
  );
}

/* ───────────────────────────── AUDIT PAGE ──────────────────────────────── */
function generateAudit(lead) {
  const ind = (lead.industry || "").toLowerCase();
  const persona = ind.includes("zubař") || ind.includes("zdrav") ? "ordinace"
    : ind.includes("gastro") || ind.includes("bistro") || ind.includes("restaur") ? "gastro"
    : ind.includes("řemeslo") || ind.includes("auto") ? "řemeslo"
    : ind.includes("krása") || ind.includes("studio") ? "služba"
    : "general";
  const samples = {
    "ordinace":  { hero: "Žádný jasný call-to-action na rezervaci.", missingOffer: "Chybí přehled výkonů a cen.", redesign: "Online rezervace + sekce o lékařích + FAQ + důvěryhodné fotky ordinace." },
    "gastro":    { hero: "Žádné fotky jídel v hero sekci, jen logo na pozadí.", missingOffer: "Chybí aktuální menu online.", redesign: "Velké fotky jídel, denní menu, online rezervace stolu, mapa." },
    "řemeslo":   { hero: "Žádný portfoliový důkaz toho co umí.", missingOffer: "Chybí ukázky práce a poptávkový formulář.", redesign: "Galerie projektů, jednoduchý formulář poptávky, reference, kontakt s mapou." },
    "služba":    { hero: "Hero sekce nepopisuje kdo a pro koho.", missingOffer: "Chybí ceník a online rezervace.", redesign: "Jasné představení služeb, online booking, transformace klientů (před/po)." },
    "general":   { hero: "Hero sekce neříká co firma dělá a komu.", missingOffer: "Není jasná hodnotová nabídka.", redesign: "Restruktura — co děláme, pro koho, proč my, sociální důkaz, CTA." },
  };
  const s = samples[persona];
  return {
    firstImpression: `Web ${lead.website || "této firmy"} působí zastarale. ${ind ? `Pro obor ${lead.industry} je standardně očekáván modernější vzhled.` : ""}`,
    heroIssue: s.hero,
    copyIssue: "Texty popisují firmu, ale neříkají co konkrétně získá zákazník.",
    ctaIssue: "Žádné jasné hlavní CTA — nikde není zjevné co má návštěvník udělat.",
    trustIssue: "Chybí reference, čísla, konkrétní lidé. Návštěvník nemá důvod uvěřit.",
    mobileIssue: "Mobilní verze není optimalizovaná, písmo malé, tlačítka miniaturní.",
    speedIssue: "Web se načítá pomalu, neoptimalizované obrázky.",
    missingRefs: "Ano — chybí.",
    missingOffer: s.missingOffer,
    score: 3,
    redesign: s.redesign,
    salesAngle: `Konkurence v ${lead.city || "okolí"} už podobné weby má. Každý měsíc bez moderního webu = ušlé poptávky.`,
  };
}

function AuditsPage({ state, setState }) {
  const [selected, setSelected] = useState(state.leads[0]?.id || null);
  const lead = state.leads.find(l => l.id === selected);
  const audit = (state.audits && state.audits[selected]) || null;

  const [draft, setDraft] = useState(audit || {
    firstImpression: "", heroIssue: "", copyIssue: "", ctaIssue: "", trustIssue: "", mobileIssue: "", speedIssue: "",
    missingRefs: "", missingOffer: "", score: 5, redesign: "", salesAngle: "",
  });

  useEffect(() => {
    setDraft(audit || {
      firstImpression: "", heroIssue: "", copyIssue: "", ctaIssue: "", trustIssue: "", mobileIssue: "", speedIssue: "",
      missingRefs: "", missingOffer: "", score: 5, redesign: "", salesAngle: "",
    });
  }, [selected]); // eslint-disable-line

  const set = (k, v) => setDraft(s => ({ ...s, [k]: v }));
  const save = () => setState(s => ({ ...s, audits: { ...s.audits, [selected]: draft } }));
  const generate = () => { if (lead) setDraft(generateAudit(lead)); };

  return (
    <div className="space-y-4">
      <div>
        <h2 className="text-[20px] font-semibold text-stone-900 tracking-tight">Website Audit</h2>
        <p className="text-[13px] text-stone-500 mt-0.5">Pro každý lead si vytvoř konkrétní audit. To je tvůj prodejní argument.</p>
      </div>

      {state.leads.length === 0 ? (
        <EmptyState icon={Eye} title="Nejprve přidej lead" hint="Audity se vážou ke konkrétním leadům. Otevři Lead Tracker a přidej první firmu." />
      ) : (
        <div className="grid grid-cols-1 lg:grid-cols-3 gap-4">
          <Card className="p-3 lg:col-span-1">
            <div className="text-[11px] uppercase tracking-wider text-stone-500 font-medium px-2 mb-2">Vyber lead</div>
            <div className="space-y-1 max-h-[600px] overflow-y-auto">
              {state.leads.map(l => (
                <button key={l.id} onClick={() => setSelected(l.id)}
                  className={`w-full text-left px-2.5 py-2 rounded-md text-[13px] flex items-center justify-between ${
                    selected === l.id ? "bg-stone-900 text-stone-50" : "hover:bg-stone-100 text-stone-700"}`}>
                  <span className="truncate">{l.company}</span>
                  {state.audits?.[l.id] && <BadgeCheck size={12} className={selected === l.id ? "text-stone-50" : "text-emerald-600"} />}
                </button>
              ))}
            </div>
          </Card>

          <Card className="p-5 lg:col-span-2">
            {lead ? (
              <>
                <div className="flex items-start justify-between mb-4 pb-4 border-b border-stone-200">
                  <div>
                    <div className="text-[11px] uppercase tracking-wider text-stone-500">Audit</div>
                    <h3 className="text-[16px] font-semibold text-stone-900">{lead.company}</h3>
                    {lead.currentSite && <a href={lead.currentSite} target="_blank" rel="noreferrer"
                      className="text-[12px] text-stone-500 hover:text-stone-900 inline-flex items-center gap-1 mt-0.5">
                      <ExternalLink size={11} />{lead.currentSite}</a>}
                  </div>
                  <Btn variant="accent" small icon={Sparkles} onClick={generate}>Vygenerovat návrh auditu</Btn>
                </div>

                <div className="grid grid-cols-2 gap-3">
                  <Field label="První dojem" full><TextArea value={draft.firstImpression} onChange={e => set("firstImpression", e.target.value)} /></Field>
                  <Field label="Problém s hero sekcí"><TextArea value={draft.heroIssue} onChange={e => set("heroIssue", e.target.value)} /></Field>
                  <Field label="Problém s textem"><TextArea value={draft.copyIssue} onChange={e => set("copyIssue", e.target.value)} /></Field>
                  <Field label="Problém s CTA"><TextArea value={draft.ctaIssue} onChange={e => set("ctaIssue", e.target.value)} /></Field>
                  <Field label="Problém s důvěryhodností"><TextArea value={draft.trustIssue} onChange={e => set("trustIssue", e.target.value)} /></Field>
                  <Field label="Problém s mobilní verzí"><TextArea value={draft.mobileIssue} onChange={e => set("mobileIssue", e.target.value)} /></Field>
                  <Field label="Problém s rychlostí / přehledností"><TextArea value={draft.speedIssue} onChange={e => set("speedIssue", e.target.value)} /></Field>
                  <Field label="Chybějící reference"><TextInput value={draft.missingRefs} onChange={e => set("missingRefs", e.target.value)} /></Field>
                  <Field label="Chybějící nabídka"><TextInput value={draft.missingOffer} onChange={e => set("missingOffer", e.target.value)} /></Field>
                  <Field label={`Celkové skóre webu: ${draft.score}/10`} full>
                    <input type="range" min={1} max={10} value={draft.score}
                      onChange={e => set("score", +e.target.value)} className="w-full accent-stone-900" />
                  </Field>
                  <Field label="Doporučený redesign" full><TextArea value={draft.redesign} onChange={e => set("redesign", e.target.value)} rows={4} /></Field>
                  <Field label="Hlavní prodejní argument pro oslovení" full><TextArea value={draft.salesAngle} onChange={e => set("salesAngle", e.target.value)} /></Field>
                </div>

                <div className="flex justify-end gap-2 mt-4 pt-4 border-t border-stone-200">
                  <Btn onClick={save} icon={Check}>Uložit audit</Btn>
                </div>
              </>
            ) : <div className="text-[13px] text-stone-500">Vyber lead vlevo.</div>}
          </Card>
        </div>
      )}
    </div>
  );
}

/* ───────────────────────────── OUTREACH PAGE ───────────────────────────── */
function fillTemplate(text, ctx) {
  return text.replace(/{{(\w+)}}/g, (_, k) => ctx[k] || `{{${k}}}`);
}
function generateColdEmail(lead, sender) {
  const problem = lead.siteRating || "váš web má prostor ke zlepšení";
  const improvement = lead.improvement || "drobné úpravy hero sekce a CTA";
  const question = "Mělo by smysl o tom 10 minut popovídat?";
  return {
    subject: `Krátká myšlenka k webu ${lead.company}`,
    body: `Dobrý den ${lead.contact || ""},

koukal jsem na ${lead.website || "váš web"} a všiml jsem si, že ${problem.toLowerCase().replace(/\.$/, "")}.

Mám pár nápadů, jak by to šlo zlepšit — konkrétně ${improvement.toLowerCase().replace(/\.$/, "")}.

${question}

${sender || "Vlastník"}`,
  };
}

function OutreachPage({ state, setState }) {
  const [selectedLead, setSelectedLead] = useState(state.leads[0]?.id || null);
  const [tab, setTab] = useState("generator"); // generator | templates
  const [editingTpl, setEditingTpl] = useState(null);
  const [generated, setGenerated] = useState(null);
  const [copied, setCopied] = useState(false);

  const lead = state.leads.find(l => l.id === selectedLead);

  const doGenerate = () => {
    if (!lead) return;
    setGenerated(generateColdEmail(lead, state.settings.myName));
  };

  const markSent = () => {
    if (!lead) return;
    setState(s => ({
      ...s,
      leads: s.leads.map(l => l.id === lead.id ? { ...l, status: "outreached", lastContact: today(), nextFollowup: addDays(today(), 4) } : l)
    }));
  };

  const copyEmail = () => {
    if (!generated) return;
    navigator.clipboard?.writeText(`Předmět: ${generated.subject}\n\n${generated.body}`);
    setCopied(true);
    setTimeout(() => setCopied(false), 1500);
  };

  const saveTpl = (tpl) => {
    setState(s => ({ ...s, templates: s.templates.some(t => t.id === tpl.id) ? s.templates.map(t => t.id === tpl.id ? tpl : t) : [tpl, ...s.templates] }));
  };
  const delTpl = (id) => setState(s => ({ ...s, templates: s.templates.filter(t => t.id !== id) }));

  return (
    <div className="space-y-4">
      <div className="flex items-end justify-between flex-wrap gap-3">
        <div>
          <h2 className="text-[20px] font-semibold text-stone-900 tracking-tight">Outreach Center</h2>
          <p className="text-[13px] text-stone-500 mt-0.5">Krátké, lidské e-maily. Cílem je odpověď, ne hned prodej.</p>
        </div>
        <div className="flex bg-stone-100 rounded-md p-0.5">
          <button onClick={() => setTab("generator")} className={`px-3 py-1 text-[12px] rounded ${tab === "generator" ? "bg-white shadow-sm text-stone-900" : "text-stone-500"}`}>Generátor</button>
          <button onClick={() => setTab("templates")} className={`px-3 py-1 text-[12px] rounded ${tab === "templates" ? "bg-white shadow-sm text-stone-900" : "text-stone-500"}`}>Šablony</button>
        </div>
      </div>

      {tab === "generator" ? (
        state.leads.length === 0 ? (
          <EmptyState icon={Mail} title="Nejprve přidej lead" hint="Generátor se vždy vztahuje ke konkrétnímu leadu." />
        ) : (
          <div className="grid grid-cols-1 lg:grid-cols-3 gap-4">
            <Card className="p-3 lg:col-span-1">
              <div className="text-[11px] uppercase tracking-wider text-stone-500 font-medium px-2 mb-2">Vyber lead</div>
              <div className="space-y-1 max-h-[600px] overflow-y-auto">
                {state.leads.map(l => (
                  <button key={l.id} onClick={() => { setSelectedLead(l.id); setGenerated(null); }}
                    className={`w-full text-left px-2.5 py-2 rounded-md text-[13px] ${
                      selectedLead === l.id ? "bg-stone-900 text-stone-50" : "hover:bg-stone-100 text-stone-700"}`}>
                    <div className="truncate">{l.company}</div>
                    <div className={`text-[11px] mt-0.5 ${selectedLead === l.id ? "text-stone-300" : "text-stone-500"}`}>
                      <StatusPill list={LEAD_STATUSES} id={l.status} />
                    </div>
                  </button>
                ))}
              </div>
            </Card>

            <Card className="p-5 lg:col-span-2">
              {lead && (
                <>
                  <div className="flex items-start justify-between pb-4 border-b border-stone-200 mb-4">
                    <div>
                      <div className="text-[11px] uppercase tracking-wider text-stone-500">Pro</div>
                      <h3 className="text-[16px] font-semibold text-stone-900">{lead.company}</h3>
                      <div className="text-[12px] text-stone-500 mt-0.5">{lead.email || "—"} · {lead.contact || "—"}</div>
                    </div>
                    <Btn variant="accent" icon={Sparkles} onClick={doGenerate}>Vygenerovat e-mail</Btn>
                  </div>

                  {!generated ? (
                    <div className="text-[13px] text-stone-500">
                      Klikni na <span className="font-medium text-stone-700">Vygenerovat e-mail</span>. Použiju data z auditu a údaje o leadu.
                      Styl: krátký, lidský, bez korporátních frází, s otázkou na konci.
                    </div>
                  ) : (
                    <div className="space-y-3">
                      <Field label="Předmět"><TextInput value={generated.subject} onChange={e => setGenerated(g => ({ ...g, subject: e.target.value }))} /></Field>
                      <Field label="Tělo">
                        <textarea rows={12} value={generated.body} onChange={e => setGenerated(g => ({ ...g, body: e.target.value }))}
                          className={inputCls + " font-mono text-[12px]"} />
                      </Field>
                      <div className="flex justify-end gap-2 pt-2 border-t border-stone-200">
                        <Btn variant="secondary" onClick={copyEmail} icon={copied ? Check : Copy}>{copied ? "Zkopírováno" : "Kopírovat"}</Btn>
                        <Btn onClick={markSent} icon={Mail}>Označit jako odeslaný</Btn>
                      </div>
                    </div>
                  )}
                </>
              )}
            </Card>
          </div>
        )
      ) : (
        <div className="space-y-3">
          <div className="flex justify-end">
            <Btn icon={Plus} onClick={() => setEditingTpl({ id: uid(), name: "", type: "cold", subject: "", body: "" })}>Nová šablona</Btn>
          </div>
          {state.templates.length === 0 ? (
            <EmptyState icon={Mail} title="Žádné šablony" hint="Vytvoř si sadu šablon pro různé typy oslovení." />
          ) : (
            <div className="grid grid-cols-1 md:grid-cols-2 gap-3">
              {state.templates.map(t => (
                <Card key={t.id} className="p-4">
                  <div className="flex items-start justify-between">
                    <div>
                      <div className="text-[11px] uppercase tracking-wider text-stone-500">{t.type === "cold" ? "Cold e-mail" : "Follow-up"}</div>
                      <div className="font-medium text-stone-900 text-[14px] mt-0.5">{t.name || "Bez názvu"}</div>
                    </div>
                    <div>
                      <IconBtn icon={Edit3} onClick={() => setEditingTpl(t)} />
                      <IconBtn icon={Trash2} danger onClick={() => { if (confirm("Smazat?")) delTpl(t.id); }} />
                    </div>
                  </div>
                  <div className="text-[12px] text-stone-700 mt-2 font-medium">{t.subject}</div>
                  <pre className="text-[11px] text-stone-500 mt-1 whitespace-pre-wrap font-mono leading-relaxed line-clamp-5">{t.body}</pre>
                </Card>
              ))}
            </div>
          )}
        </div>
      )}

      <Modal open={!!editingTpl} onClose={() => setEditingTpl(null)} title="Šablona e-mailu" wide>
        {editingTpl && (
          <div className="space-y-3">
            <div className="grid grid-cols-2 gap-3">
              <Field label="Název"><TextInput value={editingTpl.name} onChange={e => setEditingTpl(s => ({ ...s, name: e.target.value }))} /></Field>
              <Field label="Typ"><Select value={editingTpl.type} onChange={e => setEditingTpl(s => ({ ...s, type: e.target.value }))}
                options={[{ id: "cold", label: "Cold e-mail" }, { id: "fu", label: "Follow-up" }]} /></Field>
              <Field label="Předmět" full><TextInput value={editingTpl.subject} onChange={e => setEditingTpl(s => ({ ...s, subject: e.target.value }))} /></Field>
              <Field label="Tělo (lze použít {{company}}, {{contact}}, {{website}}, {{problem}}, {{improvement}}, {{senderName}})" full>
                <textarea rows={10} value={editingTpl.body} onChange={e => setEditingTpl(s => ({ ...s, body: e.target.value }))} className={inputCls + " font-mono text-[12px]"} />
              </Field>
            </div>
            <div className="flex justify-end gap-2 pt-2 border-t border-stone-200">
              <Btn variant="secondary" onClick={() => setEditingTpl(null)}>Zrušit</Btn>
              <Btn onClick={() => { saveTpl(editingTpl); setEditingTpl(null); }}>Uložit</Btn>
            </div>
          </div>
        )}
      </Modal>
    </div>
  );
}

/* ─────────────────────────────── DEALS PAGE ─────────────────────────────── */
function DealsPage({ state, setState }) {
  const [editing, setEditing] = useState(null);
  const [creating, setCreating] = useState(false);

  const totalExpected = state.deals
    .filter(d => !["won","lost"].includes(d.status))
    .reduce((s,d) => s + (d.monthly * (d.probability/100)), 0);
  const totalMonthly = state.deals.filter(d => !["won","lost"].includes(d.status)).reduce((s,d) => s + d.monthly, 0);

  const saveDeal = (d) => setState(s => ({ ...s, deals: s.deals.some(x => x.id === d.id) ? s.deals.map(x => x.id === d.id ? d : x) : [d, ...s.deals] }));
  const delDeal = (id) => setState(s => ({ ...s, deals: s.deals.filter(d => d.id !== id) }));

  return (
    <div className="space-y-4">
      <div className="flex items-end justify-between flex-wrap gap-3">
        <div>
          <h2 className="text-[20px] font-semibold text-stone-900 tracking-tight">Sales Pipeline</h2>
          <p className="text-[13px] text-stone-500 mt-0.5">{state.deals.length} dealů · {fmtMoney(Math.round(totalExpected))} vážená pipeline · {fmtMoney(totalMonthly)} potenciál</p>
        </div>
        <Btn icon={Plus} onClick={() => setCreating(true)}>Nový deal</Btn>
      </div>

      {state.deals.length === 0 ? (
        <EmptyState icon={Briefcase} title="Žádné dealy" hint="Když lead odpoví a začnete řešit konkrétní spolupráci, převeď ho na deal."
          action={<Btn icon={Plus} onClick={() => setCreating(true)}>Vytvořit první deal</Btn>} />
      ) : (
        <div className="overflow-x-auto pb-2">
          <div className="flex gap-3 min-w-max">
            {DEAL_STATUSES.map(s => {
              const items = state.deals.filter(d => d.status === s.id);
              const t = TONE_STYLES[s.tone] || TONE_STYLES.stone;
              const sum = items.reduce((acc, d) => acc + d.monthly * (d.probability/100), 0);
              return (
                <div key={s.id} className="w-72 shrink-0">
                  <div className={`flex items-center justify-between mb-2 px-2.5 py-1.5 rounded-md ${t.bg}`}>
                    <div className={`text-[12px] font-medium ${t.text}`}>{s.label}</div>
                    <div className={`text-[11px] tabular-nums ${t.text} opacity-80`}>{items.length} · {fmtMoney(Math.round(sum))}</div>
                  </div>
                  <div className="space-y-2">
                    {items.map(d => {
                      const lead = state.leads.find(l => l.id === d.leadId);
                      return (
                        <div key={d.id} onClick={() => setEditing(d)}
                          className="bg-white rounded-md ring-1 ring-stone-200 p-3 cursor-pointer hover:ring-stone-300">
                          <div className="font-medium text-[13px] text-stone-900 truncate">{lead?.company || "Bez leadu"}</div>
                          <div className="flex items-center gap-2 mt-1.5">
                            <div className="text-[11px] text-stone-600 tabular-nums">{fmtMoney(d.monthly)}/měs</div>
                            <div className="text-[11px] text-stone-400">·</div>
                            <div className="text-[11px] text-stone-500 tabular-nums">{d.probability}%</div>
                          </div>
                          <div className="mt-2 h-1 bg-stone-100 rounded-full overflow-hidden">
                            <div className="h-full bg-stone-700 rounded-full" style={{ width: `${d.probability}%` }} />
                          </div>
                          {d.nextStep && <div className="mt-2 text-[11px] text-stone-500 truncate">→ {d.nextStep}</div>}
                        </div>
                      );
                    })}
                    {items.length === 0 && <div className="text-[11px] text-stone-400 text-center py-4 border border-dashed border-stone-200 rounded-md">Prázdné</div>}
                  </div>
                </div>
              );
            })}
          </div>
        </div>
      )}

      <Modal open={creating || !!editing} onClose={() => { setCreating(false); setEditing(null); }} title={editing ? "Upravit deal" : "Nový deal"}>
        <DealForm initial={editing} leads={state.leads}
          onSave={d => { saveDeal(d); setCreating(false); setEditing(null); }}
          onClose={() => { setCreating(false); setEditing(null); }}
          onDelete={editing ? () => { delDeal(editing.id); setEditing(null); } : null} />
      </Modal>
    </div>
  );
}

function DealForm({ initial, leads, onSave, onClose, onDelete }) {
  const [f, setF] = useState(initial || {
    id: uid(), leadId: leads[0]?.id || "", status: "new", monthly: 3500, setup: 9000,
    probability: 50, lastActivity: today(), nextStep: "", note: "",
  });
  const set = (k,v) => setF(s => ({ ...s, [k]: v }));
  return (
    <div className="space-y-3">
      <div className="grid grid-cols-2 gap-3">
        <Field label="Lead / klient" full>
          <Select value={f.leadId} onChange={e => set("leadId", e.target.value)}
            options={leads.map(l => ({ id: l.id, label: l.company }))} />
        </Field>
        <Field label="Stav"><Select value={f.status} onChange={e => set("status", e.target.value)} options={DEAL_STATUSES} /></Field>
        <Field label="Pravděpodobnost (%)"><NumberInput value={f.probability} onChange={e => set("probability", +e.target.value)} min={0} max={100}/></Field>
        <Field label="Měsíční cena"><NumberInput value={f.monthly} onChange={e => set("monthly", +e.target.value)} /></Field>
        <Field label="Setup fee"><NumberInput value={f.setup} onChange={e => set("setup", +e.target.value)} /></Field>
        <Field label="Datum poslední aktivity"><DateInput value={f.lastActivity} onChange={e => set("lastActivity", e.target.value)} /></Field>
        <Field label="Další krok"><TextInput value={f.nextStep} onChange={e => set("nextStep", e.target.value)} placeholder="Zavolat zítra v 10:00" /></Field>
        <Field label="Poznámka" full><TextArea value={f.note} onChange={e => set("note", e.target.value)} /></Field>
      </div>
      <div className="flex justify-between pt-2 border-t border-stone-200">
        <div>{onDelete && <Btn variant="danger" small onClick={() => { if (confirm("Smazat?")) onDelete(); }} icon={Trash2}>Smazat</Btn>}</div>
        <div className="flex gap-2">
          <Btn variant="secondary" onClick={onClose}>Zrušit</Btn>
          <Btn onClick={() => onSave(f)}>Uložit</Btn>
        </div>
      </div>
    </div>
  );
}

/* ────────────────────────────── CLIENTS PAGE ────────────────────────────── */
function ClientsPage({ state, setState }) {
  const [editing, setEditing] = useState(null);
  const [creating, setCreating] = useState(false);

  const saveClient = (c) => setState(s => ({ ...s, clients: s.clients.some(x => x.id === c.id) ? s.clients.map(x => x.id === c.id ? c : x) : [c, ...s.clients] }));
  const delClient = (id) => setState(s => ({ ...s, clients: s.clients.filter(c => c.id !== id) }));

  return (
    <div className="space-y-4">
      <div className="flex items-end justify-between flex-wrap gap-3">
        <div>
          <h2 className="text-[20px] font-semibold text-stone-900 tracking-tight">Klienti</h2>
          <p className="text-[13px] text-stone-500 mt-0.5">{state.clients.length} aktivních klientů</p>
        </div>
        <Btn icon={Plus} onClick={() => setCreating(true)}>Nový klient</Btn>
      </div>

      {state.clients.length === 0 ? (
        <EmptyState icon={UserCheck} title="Zatím žádní klienti" hint="Až podepíšeš první deal, převeď ho sem na klienta."
          action={<Btn icon={Plus} onClick={() => setCreating(true)}>Přidat klienta</Btn>} />
      ) : (
        <div className="grid grid-cols-1 md:grid-cols-2 gap-3">
          {state.clients.map(c => {
            const d = daysFromToday(c.nextPayment);
            const overdue = c.paymentStatus === "Po splatnosti";
            return (
              <Card key={c.id} className="p-5">
                <div className="flex items-start justify-between">
                  <div className="min-w-0">
                    <div className="flex items-center gap-2">
                      <h3 className="text-[15px] font-semibold text-stone-900 truncate">{c.company}</h3>
                      <span className="px-1.5 py-0.5 rounded text-[10px] font-medium bg-stone-100 text-stone-600 ring-1 ring-stone-200">{c.package}</span>
                    </div>
                    <a href={`https://${c.domain}`} target="_blank" rel="noreferrer"
                      className="text-[12px] text-stone-500 hover:text-stone-900 inline-flex items-center gap-1 mt-0.5">
                      <Globe size={11} />{c.domain}</a>
                  </div>
                  <div>
                    <IconBtn icon={Edit3} onClick={() => setEditing(c)} />
                    <IconBtn icon={Trash2} danger onClick={() => { if (confirm("Smazat?")) delClient(c.id); }} />
                  </div>
                </div>

                <div className="grid grid-cols-2 gap-3 mt-4 pt-4 border-t border-stone-100">
                  <div>
                    <div className="text-[11px] uppercase tracking-wider text-stone-500">Měsíční</div>
                    <div className="text-[17px] font-semibold tabular-nums text-stone-900 mt-0.5">{fmtMoney(c.monthly)}</div>
                  </div>
                  <div>
                    <div className="text-[11px] uppercase tracking-wider text-stone-500">Další platba</div>
                    <div className={`text-[13px] mt-0.5 ${overdue ? "text-red-700 font-medium" : "text-stone-700"}`}>
                      {c.nextPayment ? (overdue ? `${Math.abs(d)}d po splatnosti` : d === 0 ? "Dnes" : `Za ${d} dní`) : "—"}
                    </div>
                  </div>
                </div>

                <div className="flex flex-wrap gap-1.5 mt-3">
                  <span className={`px-2 py-0.5 rounded-md text-[11px] font-medium ring-1 ring-inset ${
                    overdue ? "bg-red-50 text-red-800 ring-red-200" :
                    c.paymentStatus === "Zaplaceno" ? "bg-emerald-50 text-emerald-800 ring-emerald-200" :
                    c.paymentStatus === "Čeká na platbu" ? "bg-amber-50 text-amber-800 ring-amber-200" :
                    "bg-stone-100 text-stone-700 ring-stone-200"
                  }`}>{c.paymentStatus}</span>
                  <span className="px-2 py-0.5 rounded-md text-[11px] font-medium ring-1 ring-inset bg-stone-50 text-stone-700 ring-stone-200">
                    Web: {c.siteStatus}
                  </span>
                </div>

                {c.requests?.length > 0 && (
                  <div className="mt-3 pt-3 border-t border-stone-100">
                    <div className="text-[11px] uppercase tracking-wider text-stone-500 mb-1.5">Aktivní požadavky</div>
                    <ul className="space-y-1">
                      {c.requests.map((r, i) => (
                        <li key={i} className="text-[12px] text-stone-700 flex items-start gap-1.5">
                          <CircleDot size={10} className="text-stone-400 mt-1 shrink-0" />
                          <span>{r}</span>
                        </li>
                      ))}
                    </ul>
                  </div>
                )}
              </Card>
            );
          })}
        </div>
      )}

      <Modal open={creating || !!editing} onClose={() => { setCreating(false); setEditing(null); }} title={editing ? "Upravit klienta" : "Nový klient"} wide>
        <ClientForm initial={editing}
          onSave={c => { saveClient(c); setCreating(false); setEditing(null); }}
          onClose={() => { setCreating(false); setEditing(null); }}
          onDelete={editing ? () => { delClient(editing.id); setEditing(null); } : null} />
      </Modal>
    </div>
  );
}

function ClientForm({ initial, onSave, onClose, onDelete }) {
  const [f, setF] = useState(initial || {
    id: uid(), company: "", domain: "", package: "Standard", monthly: 3500, setup: 9000,
    startDate: today(), nextPayment: addDays(today(), 30), paymentStatus: "Čeká na platbu",
    siteStatus: "Návrh", notes: "", accessNote: "", requests: [], history: [],
  });
  const [newReq, setNewReq] = useState("");
  const set = (k,v) => setF(s => ({ ...s, [k]: v }));
  const addReq = () => { if (!newReq.trim()) return; setF(s => ({ ...s, requests: [...(s.requests||[]), newReq.trim()] })); setNewReq(""); };
  const rmReq = (i) => setF(s => ({ ...s, requests: s.requests.filter((_, idx) => idx !== i) }));
  return (
    <div className="space-y-3">
      <div className="grid grid-cols-2 gap-3">
        <Field label="Název firmy"><TextInput value={f.company} onChange={e => set("company", e.target.value)} /></Field>
        <Field label="Doména"><TextInput value={f.domain} onChange={e => set("domain", e.target.value)} placeholder="firma.cz" /></Field>
        <Field label="Balíček"><Select value={f.package} onChange={e => set("package", e.target.value)} options={PACKAGES} /></Field>
        <Field label="Měsíční cena"><NumberInput value={f.monthly} onChange={e => set("monthly", +e.target.value)} /></Field>
        <Field label="Setup fee"><NumberInput value={f.setup} onChange={e => set("setup", +e.target.value)} /></Field>
        <Field label="Začátek spolupráce"><DateInput value={f.startDate} onChange={e => set("startDate", e.target.value)} /></Field>
        <Field label="Další platba"><DateInput value={f.nextPayment} onChange={e => set("nextPayment", e.target.value)} /></Field>
        <Field label="Stav platby"><Select value={f.paymentStatus} onChange={e => set("paymentStatus", e.target.value)} options={PAYMENT_STATES} /></Field>
        <Field label="Stav webu"><Select value={f.siteStatus} onChange={e => set("siteStatus", e.target.value)} options={WEBSITE_STATES} /></Field>
        <Field label="Poznámky" full><TextArea value={f.notes} onChange={e => set("notes", e.target.value)} /></Field>
        <Field label="Bezpečná poznámka / přístupy (placeholder — nikdy zde neukládej hesla v plain textu)" full>
          <TextArea value={f.accessNote} onChange={e => set("accessNote", e.target.value)} placeholder="např. odkaz na 1Password vault, registrar, hosting…" /></Field>
        <div className="col-span-2">
          <div className="text-[11px] uppercase tracking-wider text-stone-500 font-medium mb-1.5">Aktivní požadavky</div>
          <div className="space-y-1.5 mb-2">
            {f.requests?.map((r, i) => (
              <div key={i} className="flex items-center gap-2 px-2.5 py-1.5 bg-stone-50 rounded-md">
                <CircleDot size={11} className="text-stone-400 shrink-0" />
                <span className="text-[13px] flex-1">{r}</span>
                <button onClick={() => rmReq(i)} className="text-stone-400 hover:text-red-700"><X size={12} /></button>
              </div>
            ))}
          </div>
          <div className="flex gap-2">
            <input value={newReq} onChange={e => setNewReq(e.target.value)} onKeyDown={e => e.key === "Enter" && (e.preventDefault(), addReq())}
              placeholder="Přidat požadavek..." className={inputCls} />
            <Btn variant="secondary" onClick={addReq} icon={Plus} small>Přidat</Btn>
          </div>
        </div>
      </div>
      <div className="flex justify-between pt-2 border-t border-stone-200">
        <div>{onDelete && <Btn variant="danger" small onClick={() => { if (confirm("Smazat?")) onDelete(); }} icon={Trash2}>Smazat</Btn>}</div>
        <div className="flex gap-2">
          <Btn variant="secondary" onClick={onClose}>Zrušit</Btn>
          <Btn onClick={() => onSave(f)}>Uložit</Btn>
        </div>
      </div>
    </div>
  );
}

/* ────────────────────────────── PROJECTS PAGE ──────────────────────────── */
function ProjectsPage({ state, setState }) {
  const [editing, setEditing] = useState(null);
  const [creating, setCreating] = useState(false);
  const [showChecklist, setShowChecklist] = useState(false);

  const saveTask = (t) => setState(s => ({ ...s, tasks: s.tasks.some(x => x.id === t.id) ? s.tasks.map(x => x.id === t.id ? t : x) : [t, ...s.tasks] }));
  const delTask = (id) => setState(s => ({ ...s, tasks: s.tasks.filter(t => t.id !== id) }));
  const moveTask = (id, status) => setState(s => ({ ...s, tasks: s.tasks.map(t => t.id === id ? { ...t, status } : t) }));

  const addChecklist = (clientId) => {
    const newTasks = PROJECT_CHECKLIST.map(title => ({
      id: uid(), title, clientId, priority: "med", deadline: "", status: "backlog", note: "",
    }));
    setState(s => ({ ...s, tasks: [...newTasks, ...s.tasks] }));
    setShowChecklist(false);
  };

  return (
    <div className="space-y-4">
      <div className="flex items-end justify-between flex-wrap gap-3">
        <div>
          <h2 className="text-[20px] font-semibold text-stone-900 tracking-tight">Project Board</h2>
          <p className="text-[13px] text-stone-500 mt-0.5">{state.tasks.length} úkolů celkem</p>
        </div>
        <div className="flex gap-2">
          <Btn variant="secondary" icon={ListChecks} onClick={() => setShowChecklist(true)}>WAAS Checklist</Btn>
          <Btn icon={Plus} onClick={() => setCreating(true)}>Nový úkol</Btn>
        </div>
      </div>

      {state.tasks.length === 0 ? (
        <EmptyState icon={ListChecks} title="Žádné úkoly"
          hint="Přidej si první úkol, nebo vlož celý WAAS checklist pro nového klienta — 13 kroků od podkladů po publikaci."
          action={<Btn icon={Plus} onClick={() => setCreating(true)}>Nový úkol</Btn>} />
      ) : (
        <div className="overflow-x-auto pb-2">
          <div className="flex gap-3 min-w-max">
            {TASK_STATUSES.map(s => {
              const items = state.tasks.filter(t => t.status === s.id);
              const t = TONE_STYLES[s.tone] || TONE_STYLES.stone;
              return (
                <div key={s.id} className="w-72 shrink-0">
                  <div className={`flex items-center justify-between mb-2 px-2.5 py-1.5 rounded-md ${t.bg}`}>
                    <div className={`text-[12px] font-medium ${t.text}`}>{s.label}</div>
                    <div className={`text-[11px] ${t.text} opacity-70`}>{items.length}</div>
                  </div>
                  <div className="space-y-2">
                    {items.map(task => {
                      const client = state.clients.find(c => c.id === task.clientId);
                      const d = daysFromToday(task.deadline);
                      return (
                        <div key={task.id} onClick={() => setEditing(task)}
                          className="bg-white rounded-md ring-1 ring-stone-200 p-3 cursor-pointer hover:ring-stone-300 group">
                          <div className="font-medium text-[13px] text-stone-900">{task.title}</div>
                          {client && <div className="text-[11px] text-stone-500 mt-0.5 truncate">{client.company}</div>}
                          <div className="flex items-center justify-between mt-2">
                            <PriorityDot p={task.priority} />
                            {task.deadline && (
                              <div className={`text-[11px] tabular-nums ${d < 0 ? "text-red-700" : d === 0 ? "text-amber-700" : "text-stone-500"}`}>
                                {d < 0 ? `${Math.abs(d)}d po` : d === 0 ? "Dnes" : `+${d}d`}
                              </div>
                            )}
                          </div>
                          <div className="mt-2 hidden group-hover:flex gap-1 flex-wrap" onClick={e => e.stopPropagation()}>
                            {TASK_STATUSES.filter(x => x.id !== task.status).map(x => (
                              <button key={x.id} onClick={() => moveTask(task.id, x.id)}
                                className="text-[10px] px-1.5 py-0.5 rounded bg-stone-100 text-stone-600 hover:bg-stone-900 hover:text-stone-50">
                                → {x.label}
                              </button>
                            ))}
                          </div>
                        </div>
                      );
                    })}
                    {items.length === 0 && <div className="text-[11px] text-stone-400 text-center py-4 border border-dashed border-stone-200 rounded-md">Prázdné</div>}
                  </div>
                </div>
              );
            })}
          </div>
        </div>
      )}

      <Modal open={creating || !!editing} onClose={() => { setCreating(false); setEditing(null); }} title={editing ? "Upravit úkol" : "Nový úkol"}>
        <TaskForm initial={editing} clients={state.clients}
          onSave={t => { saveTask(t); setCreating(false); setEditing(null); }}
          onClose={() => { setCreating(false); setEditing(null); }}
          onDelete={editing ? () => { delTask(editing.id); setEditing(null); } : null} />
      </Modal>

      <Modal open={showChecklist} onClose={() => setShowChecklist(false)} title="WAAS Checklist — vlož celý projekt">
        <p className="text-[13px] text-stone-600 mb-3">Vyber klienta — vytvořím všech {PROJECT_CHECKLIST.length} úkolů typického WAAS projektu naráz.</p>
        <div className="space-y-1.5 max-h-60 overflow-y-auto mb-4">
          {state.clients.map(c => (
            <button key={c.id} onClick={() => addChecklist(c.id)}
              className="w-full text-left px-3 py-2 rounded-md hover:bg-stone-100 text-[13px] flex items-center justify-between">
              <span>{c.company}</span>
              <ChevronRight size={14} className="text-stone-400" />
            </button>
          ))}
          <button onClick={() => addChecklist(null)}
            className="w-full text-left px-3 py-2 rounded-md hover:bg-stone-100 text-[13px] flex items-center justify-between text-stone-500">
            <span>Bez klienta (obecné úkoly)</span>
            <ChevronRight size={14} className="text-stone-400" />
          </button>
        </div>
        <div className="text-[11px] text-stone-500 bg-stone-50 rounded-md p-3">
          <div className="font-medium text-stone-700 mb-1">Kroky šablony:</div>
          {PROJECT_CHECKLIST.join(" · ")}
        </div>
      </Modal>
    </div>
  );
}

function TaskForm({ initial, clients, onSave, onClose, onDelete }) {
  const [f, setF] = useState(initial || {
    id: uid(), title: "", clientId: clients[0]?.id || null, priority: "med",
    deadline: "", status: "backlog", note: "",
  });
  const set = (k,v) => setF(s => ({ ...s, [k]: v }));
  return (
    <div className="space-y-3">
      <div className="grid grid-cols-2 gap-3">
        <Field label="Název úkolu" full><TextInput value={f.title} onChange={e => set("title", e.target.value)} /></Field>
        <Field label="Klient"><Select value={f.clientId || ""} onChange={e => set("clientId", e.target.value || null)}
          options={[{ id: "", label: "—" }, ...clients.map(c => ({ id: c.id, label: c.company }))]} /></Field>
        <Field label="Priorita"><Select value={f.priority} onChange={e => set("priority", e.target.value)} options={PRIORITIES} /></Field>
        <Field label="Deadline"><DateInput value={f.deadline} onChange={e => set("deadline", e.target.value)} /></Field>
        <Field label="Stav"><Select value={f.status} onChange={e => set("status", e.target.value)} options={TASK_STATUSES} /></Field>
        <Field label="Poznámka" full><TextArea value={f.note} onChange={e => set("note", e.target.value)} /></Field>
      </div>
      <div className="flex justify-between pt-2 border-t border-stone-200">
        <div>{onDelete && <Btn variant="danger" small onClick={() => { if (confirm("Smazat?")) onDelete(); }} icon={Trash2}>Smazat</Btn>}</div>
        <div className="flex gap-2">
          <Btn variant="secondary" onClick={onClose}>Zrušit</Btn>
          <Btn onClick={() => onSave(f)}>Uložit</Btn>
        </div>
      </div>
    </div>
  );
}

/* ────────────────────────────── FINANCE PAGE ───────────────────────────── */
function FinancePage({ state, setState }) {
  const [editing, setEditing] = useState(null);
  const [creating, setCreating] = useState(false);

  const m = useMemo(() => {
    const active = state.clients.filter(c => c.paymentStatus !== "Zrušeno");
    const mrr = active.reduce((s,c) => s + (c.monthly||0), 0);
    const expectedMRR = state.deals.filter(d => !["won","lost"].includes(d.status))
      .reduce((s,d) => s + (d.monthly * d.probability/100), 0);
    const setupRevenue = state.payments.filter(p => p.type === "Setup fee" && p.status === "Zaplaceno")
      .reduce((s,p) => s + p.amount, 0);
    const avgClient = active.length ? Math.round(mrr / active.length) : 0;
    const overdue = state.payments.filter(p => p.status === "Po splatnosti");
    const thisMonth = state.payments.filter(p => {
      if (!p.dueDate) return false;
      const d = new Date(p.dueDate), n = new Date();
      return d.getMonth() === n.getMonth() && d.getFullYear() === n.getFullYear();
    });
    const churned = state.clients.filter(c => c.paymentStatus === "Zrušeno");
    return { mrr, expectedMRR, setupRevenue, avgClient, overdue, thisMonth, active, churned };
  }, [state]);

  const savePayment = (p) => setState(s => ({ ...s, payments: s.payments.some(x => x.id === p.id) ? s.payments.map(x => x.id === p.id ? p : x) : [p, ...s.payments] }));
  const delPayment = (id) => setState(s => ({ ...s, payments: s.payments.filter(p => p.id !== id) }));

  return (
    <div className="space-y-5">
      <div>
        <h2 className="text-[20px] font-semibold text-stone-900 tracking-tight">Finance & MRR</h2>
        <p className="text-[13px] text-stone-500 mt-0.5">Tvoje peníze. Buď vždycky upřímný k tomuto číslu.</p>
      </div>

      <div className="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-3">
        <Stat label="Aktuální MRR" value={fmtMoney(m.mrr)} sub={`${m.active.length} platících klientů`} icon={Wallet} accent />
        <Stat label="Očekávaný MRR (deals)" value={fmtMoney(Math.round(m.expectedMRR))} sub="vážená pipeline" icon={TrendingUp} />
        <Stat label="Setup fee (vybrané)" value={fmtMoney(m.setupRevenue)} sub="všechny zaplacené" icon={Zap} />
        <Stat label="Průměrný klient" value={fmtMoney(m.avgClient)} sub="za měsíc" icon={UserCheck} />
        <Stat label="Po splatnosti" value={m.overdue.length} sub={fmtMoney(m.overdue.reduce((s,p) => s+p.amount, 0))} icon={AlertCircle} />
        <Stat label="Platby tento měsíc" value={m.thisMonth.length} sub={fmtMoney(m.thisMonth.reduce((s,p) => s+p.amount, 0))} icon={Calendar} />
        <Stat label="Zrušení klienti" value={m.churned.length} sub="historicky" icon={ArrowDownRight} />
        <Stat label="Konverze deal→klient" value={`${state.deals.length ? Math.round(state.deals.filter(d=>d.status==='won').length/state.deals.length*100) : 0}%`} icon={BadgeCheck} />
      </div>

      <Card className="overflow-hidden">
        <div className="flex items-center justify-between px-5 py-3 border-b border-stone-200">
          <div>
            <h3 className="text-[14px] font-semibold text-stone-900">Platby</h3>
            <p className="text-[12px] text-stone-500">Měsíční předplatná, setup fee, doplňková práce.</p>
          </div>
          <Btn icon={Plus} small onClick={() => setCreating(true)}>Přidat platbu</Btn>
        </div>
        {state.payments.length === 0 ? (
          <div className="p-8"><EmptyState icon={CreditCard} title="Zatím žádné platby" hint="Až ti přijde první faktura, ulož si ji sem." /></div>
        ) : (
          <div className="overflow-x-auto">
            <table className="w-full text-[13px]">
              <thead>
                <tr className="bg-stone-50 text-stone-500 text-[11px] uppercase tracking-wider">
                  <th className="text-left px-4 py-2.5 font-medium">Klient</th>
                  <th className="text-left px-4 py-2.5 font-medium">Typ</th>
                  <th className="text-right px-4 py-2.5 font-medium">Částka</th>
                  <th className="text-left px-4 py-2.5 font-medium">Splatnost</th>
                  <th className="text-left px-4 py-2.5 font-medium">Stav</th>
                  <th className="text-left px-4 py-2.5 font-medium">Poznámka</th>
                  <th className="px-2 py-2.5"></th>
                </tr>
              </thead>
              <tbody className="divide-y divide-stone-100">
                {state.payments.sort((a,b) => new Date(b.dueDate) - new Date(a.dueDate)).map(p => {
                  const client = state.clients.find(c => c.id === p.clientId);
                  return (
                    <tr key={p.id} className="hover:bg-stone-50">
                      <td className="px-4 py-3 font-medium text-stone-800">{client?.company || "—"}</td>
                      <td className="px-4 py-3 text-stone-600">{p.type}</td>
                      <td className="px-4 py-3 text-right tabular-nums font-medium text-stone-900">{fmtMoney(p.amount)}</td>
                      <td className="px-4 py-3 text-stone-600">{p.dueDate}</td>
                      <td className="px-4 py-3">
                        <span className={`px-2 py-0.5 rounded-md text-[11px] font-medium ring-1 ring-inset ${
                          p.status === "Po splatnosti" ? "bg-red-50 text-red-800 ring-red-200" :
                          p.status === "Zaplaceno" ? "bg-emerald-50 text-emerald-800 ring-emerald-200" :
                          p.status === "Čeká na platbu" ? "bg-amber-50 text-amber-800 ring-amber-200" :
                          "bg-stone-100 text-stone-700 ring-stone-200"}`}>{p.status}</span>
                      </td>
                      <td className="px-4 py-3 text-stone-500 text-[12px] truncate max-w-[200px]">{p.note}</td>
                      <td className="px-2 py-2 text-right">
                        <IconBtn icon={Edit3} onClick={() => setEditing(p)} />
                        <IconBtn icon={Trash2} danger onClick={() => { if (confirm("Smazat?")) delPayment(p.id); }} />
                      </td>
                    </tr>
                  );
                })}
              </tbody>
            </table>
          </div>
        )}
      </Card>

      <Modal open={creating || !!editing} onClose={() => { setCreating(false); setEditing(null); }} title={editing ? "Upravit platbu" : "Nová platba"}>
        <PaymentForm initial={editing} clients={state.clients}
          onSave={p => { savePayment(p); setCreating(false); setEditing(null); }}
          onClose={() => { setCreating(false); setEditing(null); }}
          onDelete={editing ? () => { delPayment(editing.id); setEditing(null); } : null} />
      </Modal>
    </div>
  );
}

function PaymentForm({ initial, clients, onSave, onClose, onDelete }) {
  const [f, setF] = useState(initial || {
    id: uid(), clientId: clients[0]?.id || "", amount: 3500, type: "Měsíční předplatné",
    dueDate: today(), status: "Čeká na platbu", note: "",
  });
  const set = (k,v) => setF(s => ({ ...s, [k]: v }));
  return (
    <div className="space-y-3">
      <div className="grid grid-cols-2 gap-3">
        <Field label="Klient" full><Select value={f.clientId} onChange={e => set("clientId", e.target.value)}
          options={clients.map(c => ({ id: c.id, label: c.company }))} /></Field>
        <Field label="Typ"><Select value={f.type} onChange={e => set("type", e.target.value)} options={PAYMENT_TYPES} /></Field>
        <Field label="Částka"><NumberInput value={f.amount} onChange={e => set("amount", +e.target.value)} /></Field>
        <Field label="Splatnost"><DateInput value={f.dueDate} onChange={e => set("dueDate", e.target.value)} /></Field>
        <Field label="Stav"><Select value={f.status} onChange={e => set("status", e.target.value)} options={PAYMENT_STATES} /></Field>
        <Field label="Poznámka" full><TextArea value={f.note} onChange={e => set("note", e.target.value)} /></Field>
      </div>
      <div className="flex justify-between pt-2 border-t border-stone-200">
        <div>{onDelete && <Btn variant="danger" small onClick={() => { if (confirm("Smazat?")) onDelete(); }} icon={Trash2}>Smazat</Btn>}</div>
        <div className="flex gap-2">
          <Btn variant="secondary" onClick={onClose}>Zrušit</Btn>
          <Btn onClick={() => onSave(f)}>Uložit</Btn>
        </div>
      </div>
    </div>
  );
}

/* ───────────────────────────── OFFER BUILDER ───────────────────────────── */
function buildOfferText(o, currency) {
  return `Nabídka pro: ${o.clientName}

Současný stav:
${o.problem}

Navržené řešení:
${o.solution}

Rozsah:
• ${o.scope}
• Počet podstránek: ${o.pages}

Cena:
• Setup (jednorázově): ${o.setup.toLocaleString("cs-CZ")} ${currency}
• Měsíční předplatné: ${o.monthly.toLocaleString("cs-CZ")} ${currency} / měsíc

Co je v ceně:
${o.includes.split("\n").filter(Boolean).map(x => `• ${x.replace(/^[•\-]\s*/, "")}`).join("\n")}

Co není v ceně:
${o.excludes.split("\n").filter(Boolean).map(x => `• ${x.replace(/^[•\-]\s*/, "")}`).join("\n")}

Podmínky:
${o.terms}

Další krok:
${o.nextStep}
`;
}

function OffersPage({ state }) {
  const [o, setO] = useState({
    clientName: "", problem: "", solution: "",
    scope: "Moderní jednostránkový web s podstránkami, mobilní optimalizace, kontaktní formulář, hosting v ceně",
    pages: 5, monthly: state.settings.defaultMonthly, setup: state.settings.defaultSetup,
    includes: "Hosting a doména\nSSL certifikát\nMěsíční drobné úpravy (do 1h)\nZáloha webu\nE-mailová podpora",
    excludes: "Tvorba grafiky / fotek na míru\nCopywriting nad rámec dohody\nReklamní kampaně\nIntegrace třetích stran",
    terms: "Smlouva na 12 měsíců, výpověď s 1 měsíční výpovědní lhůtou. Doména a hosting jsou součástí. Po skončení spolupráce se předá funkční export webu.",
    nextStep: "Pokud nabídka dává smysl, domluvíme krátký 15min call a začneme s podklady.",
  });
  const [copied, setCopied] = useState(false);
  const set = (k,v) => setO(s => ({ ...s, [k]: v }));

  const text = buildOfferText(o, state.settings.currency);

  const fillFromClient = (id) => {
    const c = state.clients.find(x => x.id === id);
    if (!c) return;
    setO(s => ({ ...s, clientName: c.company, monthly: c.monthly, setup: c.setup }));
  };
  const fillFromLead = (id) => {
    const l = state.leads.find(x => x.id === id);
    if (!l) return;
    setO(s => ({ ...s, clientName: l.company, problem: l.siteRating, solution: l.improvement, monthly: l.monthlyValue }));
  };

  return (
    <div className="space-y-4">
      <div>
        <h2 className="text-[20px] font-semibold text-stone-900 tracking-tight">Offer Builder</h2>
        <p className="text-[13px] text-stone-500 mt-0.5">Vyplň, vygeneruj, zkopíruj. Krátká a obchodně použitelná nabídka.</p>
      </div>

      <div className="grid grid-cols-1 lg:grid-cols-2 gap-4">
        <Card className="p-5">
          <h3 className="text-[14px] font-semibold text-stone-900 mb-4">Vstupy</h3>
          <div className="grid grid-cols-2 gap-3">
            <Field label="Předvyplnit z leadu" full>
              <Select value="" onChange={e => fillFromLead(e.target.value)}
                options={[{ id: "", label: "—" }, ...state.leads.map(l => ({ id: l.id, label: l.company }))]} />
            </Field>
            <Field label="Nebo z klienta" full>
              <Select value="" onChange={e => fillFromClient(e.target.value)}
                options={[{ id: "", label: "—" }, ...state.clients.map(c => ({ id: c.id, label: c.company }))]} />
            </Field>
            <Field label="Název klienta" full><TextInput value={o.clientName} onChange={e => set("clientName", e.target.value)} /></Field>
            <Field label="Problém současného webu" full><TextArea value={o.problem} onChange={e => set("problem", e.target.value)} /></Field>
            <Field label="Navržené řešení" full><TextArea value={o.solution} onChange={e => set("solution", e.target.value)} /></Field>
            <Field label="Rozsah" full><TextInput value={o.scope} onChange={e => set("scope", e.target.value)} /></Field>
            <Field label="Počet podstránek"><NumberInput value={o.pages} onChange={e => set("pages", +e.target.value)} /></Field>
            <Field label="Měsíční cena"><NumberInput value={o.monthly} onChange={e => set("monthly", +e.target.value)} /></Field>
            <Field label="Setup fee" full><NumberInput value={o.setup} onChange={e => set("setup", +e.target.value)} /></Field>
            <Field label="Co je zahrnuto (jeden bod na řádek)" full><TextArea rows={5} value={o.includes} onChange={e => set("includes", e.target.value)} /></Field>
            <Field label="Co není zahrnuto" full><TextArea rows={4} value={o.excludes} onChange={e => set("excludes", e.target.value)} /></Field>
            <Field label="Garance / podmínky" full><TextArea rows={3} value={o.terms} onChange={e => set("terms", e.target.value)} /></Field>
            <Field label="Další krok" full><TextArea rows={2} value={o.nextStep} onChange={e => set("nextStep", e.target.value)} /></Field>
          </div>
        </Card>

        <Card className="p-5 lg:sticky lg:top-4 self-start">
          <div className="flex items-center justify-between mb-3">
            <h3 className="text-[14px] font-semibold text-stone-900">Náhled nabídky</h3>
            <Btn variant="secondary" small icon={copied ? Check : Copy}
              onClick={() => { navigator.clipboard?.writeText(text); setCopied(true); setTimeout(() => setCopied(false), 1500); }}>
              {copied ? "Zkopírováno" : "Kopírovat"}
            </Btn>
          </div>
          <pre className="text-[12px] text-stone-800 whitespace-pre-wrap font-mono leading-relaxed bg-stone-50 rounded-md p-4 ring-1 ring-stone-200 max-h-[600px] overflow-y-auto">{text}</pre>
        </Card>
      </div>
    </div>
  );
}

/* ────────────────────────────── SETTINGS PAGE ──────────────────────────── */
function SettingsPage({ state, setState }) {
  const [s, setS] = useState(state.settings);
  const [importText, setImportText] = useState("");
  const [importErr, setImportErr] = useState("");
  const fileRef = useRef(null);

  const save = () => setState(x => ({ ...x, settings: s }));
  const setF = (k,v) => setS(prev => ({ ...prev, [k]: v }));
  const setPkg = (i, k, v) => setS(prev => ({ ...prev, packages: prev.packages.map((p, idx) => idx === i ? { ...p, [k]: v } : p) }));
  const addPkg = () => setS(prev => ({ ...prev, packages: [...prev.packages, { name: "Custom", monthly: 0, setup: 0, includes: "" }] }));
  const rmPkg = (i) => setS(prev => ({ ...prev, packages: prev.packages.filter((_, idx) => idx !== i) }));

  const exportData = () => {
    const blob = new Blob([JSON.stringify(state, null, 2)], { type: "application/json" });
    const url = URL.createObjectURL(blob);
    const a = document.createElement("a");
    a.href = url; a.download = `waas-export-${today()}.json`; a.click();
    URL.revokeObjectURL(url);
  };

  const handleFile = (e) => {
    const file = e.target.files?.[0];
    if (!file) return;
    const reader = new FileReader();
    reader.onload = (ev) => setImportText(String(ev.target?.result || ""));
    reader.readAsText(file);
  };

  const doImport = () => {
    try {
      const parsed = JSON.parse(importText);
      if (!parsed.leads || !parsed.clients) throw new Error("Chybí leads / clients");
      setState(parsed);
      setImportErr("");
      setImportText("");
      alert("Data úspěšně naimportována.");
    } catch (err) {
      setImportErr("Neplatný JSON: " + err.message);
    }
  };

  const resetDemo = () => {
    if (confirm("Opravdu obnovit demo data? Všechna tvoje aktuální data budou ztracena.")) {
      setState(seedState());
    }
  };

  const wipeAll = () => {
    if (confirm("Smazat ÚPLNĚ vše a začít s prázdnou aplikací?")) {
      setState({
        leads: [], deals: [], clients: [], audits: {}, tasks: [], payments: [], templates: [],
        settings: state.settings,
      });
    }
  };

  return (
    <div className="space-y-4">
      <div>
        <h2 className="text-[20px] font-semibold text-stone-900 tracking-tight">Nastavení</h2>
        <p className="text-[13px] text-stone-500 mt-0.5">Tvoje značka, výchozí hodnoty, balíčky, data.</p>
      </div>

      <Card className="p-5">
        <h3 className="text-[14px] font-semibold text-stone-900 mb-4">Moje firma</h3>
        <div className="grid grid-cols-2 gap-3">
          <Field label="Název značky"><TextInput value={s.brand} onChange={e => setF("brand", e.target.value)} /></Field>
          <Field label="Mé jméno"><TextInput value={s.myName} onChange={e => setF("myName", e.target.value)} /></Field>
          <Field label="E-mail"><TextInput value={s.myEmail} onChange={e => setF("myEmail", e.target.value)} /></Field>
          <Field label="Měna"><TextInput value={s.currency} onChange={e => setF("currency", e.target.value)} /></Field>
          <Field label="Výchozí měsíční cena"><NumberInput value={s.defaultMonthly} onChange={e => setF("defaultMonthly", +e.target.value)} /></Field>
          <Field label="Výchozí setup fee"><NumberInput value={s.defaultSetup} onChange={e => setF("defaultSetup", +e.target.value)} /></Field>
        </div>
      </Card>

      <Card className="p-5">
        <div className="flex items-center justify-between mb-4">
          <h3 className="text-[14px] font-semibold text-stone-900">Šablony balíčků</h3>
          <Btn small variant="secondary" icon={Plus} onClick={addPkg}>Přidat balíček</Btn>
        </div>
        <div className="space-y-3">
          {s.packages.map((p, i) => (
            <div key={i} className="grid grid-cols-12 gap-2 items-start p-3 rounded-md bg-stone-50 ring-1 ring-stone-200">
              <div className="col-span-3"><Field label="Název"><TextInput value={p.name} onChange={e => setPkg(i, "name", e.target.value)} /></Field></div>
              <div className="col-span-2"><Field label="Měsíční"><NumberInput value={p.monthly} onChange={e => setPkg(i, "monthly", +e.target.value)} /></Field></div>
              <div className="col-span-2"><Field label="Setup"><NumberInput value={p.setup} onChange={e => setPkg(i, "setup", +e.target.value)} /></Field></div>
              <div className="col-span-4"><Field label="Co obsahuje"><TextInput value={p.includes} onChange={e => setPkg(i, "includes", e.target.value)} /></Field></div>
              <div className="col-span-1 pt-5"><IconBtn icon={Trash2} danger onClick={() => rmPkg(i)} /></div>
            </div>
          ))}
        </div>
      </Card>

      <div className="flex justify-end">
        <Btn onClick={save} icon={Check}>Uložit nastavení</Btn>
      </div>

      <Card className="p-5">
        <h3 className="text-[14px] font-semibold text-stone-900 mb-1">Data</h3>
        <p className="text-[12px] text-stone-500 mb-4">Export, import, reset.</p>
        <div className="flex flex-wrap gap-2 mb-4">
          <Btn variant="secondary" icon={Download} onClick={exportData}>Exportovat JSON</Btn>
          <Btn variant="secondary" icon={Upload} onClick={() => fileRef.current?.click()}>Importovat JSON</Btn>
          <Btn variant="secondary" icon={RotateCcw} onClick={resetDemo}>Obnovit demo data</Btn>
          <Btn variant="danger" icon={Trash2} onClick={wipeAll}>Smazat vše</Btn>
          <input type="file" accept="application/json" ref={fileRef} className="hidden" onChange={handleFile} />
        </div>
        {importText && (
          <div className="space-y-2">
            <textarea value={importText} onChange={e => setImportText(e.target.value)} rows={6}
              className={inputCls + " font-mono text-[11px]"} />
            {importErr && <div className="text-[12px] text-red-700">{importErr}</div>}
            <div className="flex gap-2 justify-end">
              <Btn variant="secondary" small onClick={() => { setImportText(""); setImportErr(""); }}>Zrušit</Btn>
              <Btn small onClick={doImport}>Importovat</Btn>
            </div>
          </div>
        )}
      </Card>
    </div>
  );
}

/* ──────────────────────────────── LAYOUT ───────────────────────────────── */
const NAV = [
  { id: "dashboard", label: "Dashboard", icon: LayoutDashboard },
  { id: "leads",     label: "Leady",     icon: Users },
  { id: "audits",    label: "Audity",    icon: Eye },
  { id: "outreach",  label: "Outreach",  icon: Mail },
  { id: "deals",     label: "Pipeline",  icon: Briefcase },
  { id: "clients",   label: "Klienti",   icon: UserCheck },
  { id: "projects",  label: "Projekty",  icon: ListChecks },
  { id: "finance",   label: "Finance",   icon: Wallet },
  { id: "offers",    label: "Nabídky",   icon: FileText },
  { id: "settings",  label: "Nastavení", icon: SettingsIcon },
];

function Sidebar({ page, setPage, brand, mrr, currency }) {
  return (
    <aside className="w-56 shrink-0 bg-stone-50 border-r border-stone-200 flex flex-col">
      <div className="px-4 py-5 border-b border-stone-200">
        <div className="flex items-center gap-2">
          <div className="w-7 h-7 rounded-md bg-stone-900 text-stone-50 flex items-center justify-center font-semibold text-[13px]">
            {brand[0] || "W"}
          </div>
          <div className="min-w-0">
            <div className="text-[13px] font-semibold text-stone-900 truncate">{brand}</div>
            <div className="text-[10px] text-stone-500 uppercase tracking-wider">Waas Console</div>
          </div>
        </div>
      </div>
      <nav className="flex-1 px-2 py-3 space-y-0.5">
        {NAV.map(n => (
          <button key={n.id} onClick={() => setPage(n.id)}
            className={`w-full flex items-center gap-2.5 px-2.5 py-1.5 rounded-md text-[13px] transition-colors ${
              page === n.id ? "bg-white shadow-sm ring-1 ring-stone-200 text-stone-900 font-medium"
                            : "text-stone-600 hover:bg-stone-100 hover:text-stone-900"}`}>
            <n.icon size={14} />{n.label}
          </button>
        ))}
      </nav>
      <div className="px-4 py-3 border-t border-stone-200">
        <div className="text-[10px] uppercase tracking-wider text-stone-500 font-medium">MRR</div>
        <div className="text-[16px] font-semibold text-stone-900 tabular-nums">{fmtMoney(mrr, currency)}</div>
      </div>
    </aside>
  );
}

function TopBar({ state, openLead, onQuickAdd }) {
  const [q, setQ] = useState("");
  const [open, setOpen] = useState(false);
  const results = useMemo(() => {
    if (!q) return [];
    const lq = q.toLowerCase();
    return [
      ...state.leads.filter(l => l.company.toLowerCase().includes(lq)).slice(0, 5).map(l => ({ ...l, kind: "Lead" })),
      ...state.clients.filter(c => c.company.toLowerCase().includes(lq)).slice(0, 5).map(c => ({ ...c, kind: "Klient" })),
    ];
  }, [q, state]);

  return (
    <header className="h-14 border-b border-stone-200 bg-white flex items-center px-5 gap-3 sticky top-0 z-20">
      <div className="relative flex-1 max-w-xl">
        <SearchIcon size={14} className="absolute left-3 top-2.5 text-stone-400" />
        <input value={q} onChange={e => { setQ(e.target.value); setOpen(true); }} onFocus={() => setOpen(true)}
          onBlur={() => setTimeout(() => setOpen(false), 200)}
          placeholder="Rychlé vyhledávání leadů a klientů…"
          className="w-full pl-9 pr-3 py-1.5 text-[13px] bg-stone-50 ring-1 ring-stone-200 rounded-md focus:ring-stone-400 focus:bg-white focus:outline-none" />
        {open && q && (
          <div className="absolute top-full mt-1 left-0 right-0 bg-white rounded-md ring-1 ring-stone-200 shadow-lg z-30 max-h-72 overflow-y-auto">
            {results.length === 0 ? (
              <div className="px-3 py-3 text-[12px] text-stone-500">Nic nenalezeno</div>
            ) : results.map((r, i) => (
              <button key={r.id + i} onMouseDown={() => openLead(r.kind === "Lead" ? r.id : null, r.kind)}
                className="w-full text-left px-3 py-2 hover:bg-stone-50 flex items-center justify-between text-[13px]">
                <span>{r.company}</span>
                <span className="text-[10px] uppercase tracking-wider text-stone-400">{r.kind}</span>
              </button>
            ))}
          </div>
        )}
      </div>
      <Btn icon={Plus} onClick={onQuickAdd} small>Rychlý lead</Btn>
    </header>
  );
}

/* ──────────────────────────────── ROOT APP ─────────────────────────────── */
export default function App() {
  const [state, setStateRaw] = useState(null);
  const [page, setPage] = useState("dashboard");
  const [quickLead, setQuickLead] = useState(null);
  const [openedLead, setOpenedLead] = useState(null);

  // Load
  useEffect(() => {
    let mounted = true;
    (async () => {
      const loaded = await db.load();
      if (!mounted) return;
      setStateRaw(loaded || seedState());
    })();
    return () => { mounted = false; };
  }, []);

  // Persist
  const setState = (updater) => {
    setStateRaw(prev => {
      const next = typeof updater === "function" ? updater(prev) : updater;
      db.save(next);
      return next;
    });
  };

  if (!state) {
    return <div className="min-h-screen flex items-center justify-center bg-stone-50 text-stone-400 text-[13px]">Načítám…</div>;
  }

  const mrr = state.clients.filter(c => c.paymentStatus !== "Zrušeno").reduce((s,c) => s + (c.monthly||0), 0);

  const openLead = (id, kind = "Lead") => {
    if (kind === "Klient") { setPage("clients"); return; }
    setOpenedLead(state.leads.find(l => l.id === id));
  };

  const renderPage = () => {
    switch (page) {
      case "dashboard": return <DashboardPage state={state} onGoto={setPage} />;
      case "leads":     return <LeadsPage state={state} setState={setState} openLead={(id) => setOpenedLead(state.leads.find(l => l.id === id))} />;
      case "audits":    return <AuditsPage state={state} setState={setState} />;
      case "outreach":  return <OutreachPage state={state} setState={setState} />;
      case "deals":     return <DealsPage state={state} setState={setState} />;
      case "clients":   return <ClientsPage state={state} setState={setState} />;
      case "projects":  return <ProjectsPage state={state} setState={setState} />;
      case "finance":   return <FinancePage state={state} setState={setState} />;
      case "offers":    return <OffersPage state={state} />;
      case "settings":  return <SettingsPage state={state} setState={setState} />;
      default: return null;
    }
  };

  return (
    <>
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Geist:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap');
        body, html, #root, .waas-app { font-family: 'Geist', ui-sans-serif, system-ui, -apple-system, sans-serif; }
        .waas-app .tabular-nums { font-variant-numeric: tabular-nums; font-feature-settings: "tnum"; }
        .waas-app pre, .waas-app code, .waas-app .font-mono { font-family: 'JetBrains Mono', ui-monospace, monospace; }
        .waas-app input::placeholder, .waas-app textarea::placeholder { color: #a8a29e; }
        .waas-app *::-webkit-scrollbar { width: 8px; height: 8px; }
        .waas-app *::-webkit-scrollbar-track { background: transparent; }
        .waas-app *::-webkit-scrollbar-thumb { background: #d6d3d1; border-radius: 4px; }
        .waas-app *::-webkit-scrollbar-thumb:hover { background: #a8a29e; }
      `}</style>
      <div className="waas-app min-h-screen bg-stone-100 text-stone-900 flex">
        <Sidebar page={page} setPage={setPage} brand={state.settings.brand} mrr={mrr} currency={state.settings.currency} />
        <div className="flex-1 flex flex-col min-w-0">
          <TopBar state={state} openLead={openLead} onQuickAdd={() => setQuickLead({})} />
          <main className="flex-1 p-6 overflow-x-hidden">
            <div className="max-w-7xl mx-auto">{renderPage()}</div>
          </main>
        </div>

        <Modal open={!!quickLead} onClose={() => setQuickLead(null)} title="Rychlý nový lead" wide>
          <LeadForm onSave={(l) => setState(s => ({ ...s, leads: [l, ...s.leads] }))} onClose={() => setQuickLead(null)} />
        </Modal>

        <Modal open={!!openedLead} onClose={() => setOpenedLead(null)} title="Detail leadu" wide>
          {openedLead && <LeadForm initial={openedLead}
            onSave={(l) => setState(s => ({ ...s, leads: s.leads.map(x => x.id === l.id ? l : x) }))}
            onClose={() => setOpenedLead(null)}
            onDelete={() => { setState(s => ({ ...s, leads: s.leads.filter(l => l.id !== openedLead.id) })); setOpenedLead(null); }} />}
        </Modal>
      </div>
    </>
  );
}
