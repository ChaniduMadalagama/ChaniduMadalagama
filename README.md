import React, { useState, useEffect, useRef } from 'react';
import { 
  Github, 
  Linkedin, 
  Mail, 
  Phone,
  ArrowUpRight,
  Code2, 
  Zap, 
  Terminal,
  Briefcase,
  GraduationCap,
  Layers,
  MonitorSmartphone,
  ChevronRight,
  Globe,
  Smartphone,
  ShieldCheck,
  Cpu
} from 'lucide-react';

const App = () => {
  const [scrolled, setScrolled] = useState(0);
  const [activeSection, setActiveSection] = useState('about');
  const scrollRef = useRef(null);

  useEffect(() => {
    const handleScroll = () => {
      const position = window.scrollY;
      const height = document.documentElement.scrollHeight - window.innerHeight;
      setScrolled((position / height) * 100);

      // Simple section detector
      const sections = ['about', 'work', 'projects', 'edu'];
      for (const section of sections) {
        const element = document.getElementById(section);
        if (element) {
          const rect = element.getBoundingClientRect();
          if (rect.top >= 0 && rect.top <= 300) {
            setActiveSection(section);
          }
        }
      }
    };

    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const projects = [
    { name: "Danal Mathus", type: "Service Ecosystem", desc: "Multi-tenant architecture with real-time bidding.", tech: "Flutter / Firebase" },
    { name: "Agape Social", type: "Fintech Social", desc: "Integrated Stripe Connect with social graphing.", tech: "Dart / Node.js" },
    { name: "We EV", type: "Mobility", desc: "Low-latency map clustering for charging networks.", tech: "Google Maps / IOT" },
    { name: "Savoy POS", type: "Enterprise", desc: "NFC-first ticketing with offline-first sync.", tech: "Flutter / SQL" }
  ];

  return (
    <div className="min-h-screen bg-[#0a0a0a] text-[#a1a1aa] font-sans selection:bg-[#6366f1]/30">
      {/* Texture Overlay */}
      <div className="fixed inset-0 pointer-events-none z-[99] opacity-[0.03] bg-[url('https://grainy-gradients.vercel.app/noise.svg')]" />

      {/* Progress Bar */}
      <div className="fixed top-0 left-0 h-[2px] bg-[#6366f1] z-[100] transition-all duration-150" style={{ width: `${scrolled}%` }} />

      <div className="max-w-[1400px] mx-auto flex flex-col lg:flex-row">
        
        {/* LEFT SIDE: FIXED IDENTITY */}
        <aside className="lg:w-[40%] lg:h-screen lg:sticky lg:top-0 p-8 lg:p-20 flex flex-col justify-between border-b lg:border-b-0 lg:border-r border-white/5">
          <div className="space-y-12">
            <div className="group cursor-none">
              <div className="w-12 h-12 bg-[#6366f1] rounded-full mb-8 flex items-center justify-center text-white transition-transform group-hover:scale-110 group-hover:rotate-12">
                <Code2 size={24} />
              </div>
              <h1 className="text-5xl font-black text-white tracking-tighter leading-[0.8] mb-4">
                CHANIDU<br />MADALAGAMA
              </h1>
              <p className="text-lg font-medium text-[#6366f1] uppercase tracking-[0.2em]">
                Associate Software Engineer
              </p>
            </div>

            <nav className="hidden lg:flex flex-col gap-4 text-sm font-bold uppercase tracking-widest">
              {['about', 'work', 'projects', 'edu'].map((item) => (
                <a 
                  key={item}
                  href={`#${item}`}
                  className={`flex items-center gap-4 transition-all ${activeSection === item ? 'text-white translate-x-4' : 'hover:text-white hover:translate-x-2'}`}
                >
                  <span className={`h-[1px] transition-all ${activeSection === item ? 'w-12 bg-[#6366f1]' : 'w-4 bg-white/20'}`} />
                  {item}
                </a>
              ))}
            </nav>
          </div>

          <div className="space-y-8">
            <div className="flex gap-6">
              <a href="https://github.com/chanidumadalagama" target="_blank" className="hover:text-white transition-colors"><Github size={20} /></a>
              <a href="https://linkedin.com/in/chanidu-madalagama" target="_blank" className="hover:text-white transition-colors"><Linkedin size={20} /></a>
              <a href="mailto:chanidumadalagama@gmail.com" className="hover:text-white transition-colors"><Mail size={20} /></a>
            </div>
            <div className="flex items-center gap-3 bg-white/5 p-4 rounded-2xl border border-white/5 group cursor-pointer hover:bg-white/10 transition-all">
              <div className="w-2 h-2 bg-green-500 rounded-full animate-pulse" />
              <span className="text-xs font-bold text-white uppercase tracking-widest">Available for Hire</span>
            </div>
          </div>
        </aside>

        {/* RIGHT SIDE: SCROLLABLE CONTENT */}
        <main className="lg:w-[60%] p-8 lg:p-20 space-y-40">
          
          {/* SECTION: ABOUT */}
          <section id="about" className="space-y-8 animate-in fade-in slide-in-from-bottom-10 duration-700">
            <h2 className="text-xs font-black text-white uppercase tracking-[0.4em] mb-12 flex items-center gap-4">
              <span className="w-8 h-px bg-[#6366f1]" /> Introduction
            </h2>
            <p className="text-2xl md:text-4xl font-light text-white leading-tight">
              I specialize in <span className="text-[#6366f1] font-medium italic">Flutter architecture</span> and high-performance cross-platform development. Currently optimizing mobile ecosystems at Elegant Media.
            </p>
            <p className="text-lg leading-relaxed max-w-xl">
              I don't just write code; I design systems that scale. From real-time P2P communication for university networks to mission-critical POS systems for cinemas, I focus on the intersection of technical robustness and user delight.
            </p>
            
            <div className="grid grid-cols-2 gap-4 pt-8">
              {["Clean Architecture", "REST API Expert", "Unit Testing", "Performance Tuning"].map(skill => (
                <div key={skill} className="flex items-center gap-3 text-white font-bold text-sm">
                  <Zap size={14} className="text-[#6366f1]" /> {skill}
                </div>
              ))}
            </div>
          </section>

          {/* SECTION: WORK */}
          <section id="work" className="space-y-12">
            <h2 className="text-xs font-black text-white uppercase tracking-[0.4em] mb-12 flex items-center gap-4">
              <span className="w-8 h-px bg-[#6366f1]" /> Professional Path
            </h2>
            
            <div className="space-y-20">
              {[
                { 
                  role: "Associate Software Engineer", 
                  company: "Elegant Media Sri Lanka", 
                  period: "2024 — Present", 
                  desc: "Orchestrating full-lifecycle mobile deployments. Leading code reviews and establishing unit testing standards for global scale apps." 
                },
                { 
                  role: "Flutter Developer", 
                  company: "Archmage Solutions", 
                  period: "2022 — 2023", 
                  desc: "Transformed complex UI/UX mocks into pixel-perfect Flutter components. Optimized state management for internal task-tracking tools." 
                }
              ].map((job, i) => (
                <div key={i} className="group relative">
                  <span className="absolute -left-4 top-0 text-[120px] font-black text-white/5 select-none transition-colors group-hover:text-[#6366f1]/10">0{i+1}</span>
                  <div className="relative pt-12">
                    <h3 className="text-3xl font-black text-white mb-2">{job.role}</h3>
                    <p className="text-[#6366f1] font-bold uppercase tracking-widest text-sm mb-6">{job.company} // {job.period}</p>
                    <p className="text-lg max-w-lg">{job.desc}</p>
                  </div>
                </div>
              ))}
            </div>
          </section>

          {/* SECTION: PROJECTS */}
          <section id="projects" className="space-y-12">
            <div className="flex justify-between items-end mb-12">
              <h2 className="text-xs font-black text-white uppercase tracking-[0.4em] flex items-center gap-4">
                <span className="w-8 h-px bg-[#6366f1]" /> Selected Work
              </h2>
            </div>

            <div className="grid grid-cols-1 gap-6">
              {projects.map((proj, i) => (
                <div key={i} className="group p-8 bg-white/5 border border-white/5 rounded-[2rem] hover:bg-[#6366f1] transition-all duration-500 hover:scale-[1.02] cursor-pointer relative overflow-hidden">
                   <div className="relative z-10">
                    <div className="flex justify-between items-start mb-8">
                      <span className="text-[10px] font-bold uppercase tracking-widest text-[#6366f1] bg-white group-hover:bg-black group-hover:text-white px-3 py-1 rounded-full transition-colors">
                        {proj.tech}
                      </span>
                      <ArrowUpRight size={24} className="text-white opacity-0 group-hover:opacity-100 transition-all group-hover:translate-x-1 group-hover:-translate-y-1" />
                    </div>
                    <h3 className="text-4xl font-black text-white mb-4 group-hover:tracking-wider transition-all">{proj.name}</h3>
                    <p className="text-white/60 group-hover:text-white/90 text-lg">{proj.desc}</p>
                   </div>
                   {/* Decorative background shape */}
                   <div className="absolute -right-20 -bottom-20 w-64 h-64 bg-white/5 rounded-full group-hover:bg-white/10 transition-all duration-700" />
                </div>
              ))}
            </div>
          </section>

          {/* SECTION: ACADEMIC */}
          <section id="edu" className="space-y-12">
             <h2 className="text-xs font-black text-white uppercase tracking-[0.4em] mb-12 flex items-center gap-4">
              <span className="w-8 h-px bg-[#6366f1]" /> Education
            </h2>
            <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
              {[
                { title: "MSc Digital Marketing", school: "Cambridge College", year: "2025" },
                { title: "BEng Software Engineering", school: "London Met (UK)", year: "Current" },
                { title: "BSE (Hons)", school: "Open University SL", year: "Current" },
                { title: "HND Electrical", school: "TC Ratmalana", year: "2019" }
              ].map((edu, i) => (
                <div key={i} className="p-6 border border-white/10 rounded-2xl flex flex-col justify-between hover:border-[#6366f1] transition-colors">
                   <h4 className="text-white font-bold leading-tight mb-4">{edu.title}</h4>
                   <div className="flex justify-between items-center text-[10px] font-bold uppercase tracking-widest">
                     <span className="text-[#6366f1]">{edu.school}</span>
                     <span>{edu.year}</span>
                   </div>
                </div>
              ))}
            </div>
          </section>

          {/* FOOTER */}
          <footer className="pt-20 pb-10 border-t border-white/5 flex flex-col md:flex-row justify-between items-center gap-8">
            <p className="text-xs font-bold tracking-widest uppercase">© {new Date().getFullYear()} Chanidu Madalagama</p>
            <div className="flex gap-8">
              <a href={`tel:0770459266`} className="text-xs font-black text-white uppercase tracking-[0.2em] hover:text-[#6366f1] transition-colors">Call</a>
              <a href={`mailto:chanidumadalagama@gmail.com`} className="text-xs font-black text-white uppercase tracking-[0.2em] hover:text-[#6366f1] transition-colors">Email</a>
            </div>
          </footer>
        </main>
      </div>

      {/* CUSTOM CURSOR REPLACEMENT (Logic only, UI via CSS) */}
      <style dangerouslySetInnerHTML={{ __html: `
        @import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;700&display=swap');
        
        body {
          font-family: 'Space Grotesk', sans-serif;
          scroll-behavior: smooth;
        }

        ::-webkit-scrollbar {
          width: 5px;
        }
        ::-webkit-scrollbar-track {
          background: #0a0a0a;
        }
        ::-webkit-scrollbar-thumb {
          background: #262626;
          border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb:hover {
          background: #6366f1;
        }
      `}} />
    </div>
  );
};

export default App;
