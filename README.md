import React, { useState, useEffect } from 'react';
import { Code2, Smartphone, Globe, Award, Zap, Terminal, ChevronRight, Github, Linkedin, Mail, ExternalLink } from 'lucide-react';

export default function GitHubProfileShowcase() {
  const [mousePosition, setMousePosition] = useState({ x: 0, y: 0 });
  const [activeSection, setActiveSection] = useState('hero');
  const [typedText, setTypedText] = useState('');
  const [currentRole, setCurrentRole] = useState(0);
  
  const roles = [
    "Full Stack Developer",
    "Mobile App Developer",
    "Problem Solver",
    "Tech Enthusiast"
  ];

  // Typing animation
  useEffect(() => {
    const currentText = roles[currentRole];
    let index = 0;
    const typingInterval = setInterval(() => {
      if (index <= currentText.length) {
        setTypedText(currentText.slice(0, index));
        index++;
      } else {
        clearInterval(typingInterval);
        setTimeout(() => {
          setCurrentRole((prev) => (prev + 1) % roles.length);
        }, 2000);
      }
    }, 100);

    return () => clearInterval(typingInterval);
  }, [currentRole]);

  // Mouse tracking for parallax effect
  useEffect(() => {
    const handleMouseMove = (e) => {
      setMousePosition({
        x: (e.clientX / window.innerWidth) * 20 - 10,
        y: (e.clientY / window.innerHeight) * 20 - 10
      });
    };
    window.addEventListener('mousemove', handleMouseMove);
    return () => window.removeEventListener('mousemove', handleMouseMove);
  }, []);

  const skills = [
    { name: 'C#', color: 'from-purple-500 to-pink-500', icon: '💎' },
    { name: 'JavaScript', color: 'from-yellow-400 to-orange-500', icon: '⚡' },
    { name: 'Flutter', color: 'from-blue-400 to-cyan-500', icon: '📱' },
    { name: 'React', color: 'from-cyan-400 to-blue-500', icon: '⚛️' },
    { name: 'ASP.NET', color: 'from-green-500 to-emerald-600', icon: '🌐' },
    { name: 'SQL Server', color: 'from-red-500 to-pink-600', icon: '🗄️' },
    { name: 'Firebase', color: 'from-amber-400 to-orange-600', icon: '🔥' },
    { name: 'Java', color: 'from-red-600 to-orange-700', icon: '☕' }
  ];

  const projects = [
    { name: 'Mobile Apps', count: '10+', icon: Smartphone, color: 'bg-gradient-to-br from-purple-500 to-pink-600' },
    { name: 'Web Apps', count: '15+', icon: Globe, color: 'bg-gradient-to-br from-blue-500 to-cyan-600' },
    { name: 'DSA Problems', count: '200+', icon: Terminal, color: 'bg-gradient-to-br from-green-500 to-emerald-600' },
    { name: 'Achievements', count: '25+', icon: Award, color: 'bg-gradient-to-br from-amber-500 to-orange-600' }
  ];

  const codingPlatforms = [
    { name: 'LeetCode', url: 'https://leetcode.com/u/shubham_chaudhari_1807/', color: 'bg-orange-500', hoverColor: 'hover:bg-orange-600' },
    { name: 'GeeksforGeeks', url: 'https://www.geeksforgeeks.org/user/shubhamchahese/', color: 'bg-green-600', hoverColor: 'hover:bg-green-700' },
    { name: 'CodeChef', url: 'https://www.codechef.com/users/rcp_211101018', color: 'bg-amber-700', hoverColor: 'hover:bg-amber-800' }
  ];

  return (
    <div className="min-h-screen bg-gradient-to-br from-slate-900 via-purple-900 to-slate-900 text-white overflow-hidden">
      {/* Animated background particles */}
      <div className="fixed inset-0 overflow-hidden pointer-events-none">
        {[...Array(30)].map((_, i) => (
          <div
            key={i}
            className="absolute rounded-full bg-white opacity-10 animate-pulse"
            style={{
              width: Math.random() * 4 + 2 + 'px',
              height: Math.random() * 4 + 2 + 'px',
              top: Math.random() * 100 + '%',
              left: Math.random() * 100 + '%',
              animationDelay: Math.random() * 3 + 's',
              animationDuration: Math.random() * 3 + 2 + 's'
            }}
          />
        ))}
      </div>

      {/* Hero Section */}
      <div className="relative container mx-auto px-6 py-20">
        <div 
          className="text-center transform transition-transform duration-300"
          style={{
            transform: `translate(${mousePosition.x * 0.5}px, ${mousePosition.y * 0.5}px)`
          }}
        >
          <div className="inline-block mb-8 relative">
            <div className="absolute inset-0 bg-gradient-to-r from-cyan-400 via-purple-500 to-pink-500 rounded-full blur-2xl opacity-60 animate-pulse"></div>
            <div className="relative bg-gradient-to-r from-cyan-400 via-purple-500 to-pink-500 p-1 rounded-full">
              <div className="bg-slate-900 rounded-full p-2">
                <Code2 className="w-20 h-20 text-cyan-400 animate-bounce" />
              </div>
            </div>
          </div>
          
          <h1 className="text-6xl md:text-8xl font-bold mb-6 bg-gradient-to-r from-cyan-400 via-purple-400 to-pink-400 bg-clip-text text-transparent animate-gradient">
            Shubham Chaudhari
          </h1>
          
          <div className="text-3xl md:text-4xl font-semibold mb-8 h-16 flex items-center justify-center">
            <span className="bg-gradient-to-r from-green-400 to-cyan-400 bg-clip-text text-transparent">
              {typedText}
              <span className="animate-pulse">|</span>
            </span>
          </div>

          {/* Contact Buttons */}
          <div className="flex flex-wrap justify-center gap-4 mb-8">
            <a 
              href="mailto:chaudharishubham1807@gmail.com"
              className="flex items-center gap-2 px-6 py-3 bg-gradient-to-r from-cyan-500 to-blue-600 rounded-full hover:scale-110 transition-transform duration-300 shadow-lg hover:shadow-cyan-500/50"
            >
              <Mail className="w-5 h-5" />
              Email Me
            </a>
            <a 
              href="https://shubhamportfoliosite.netlify.app"
              target="_blank"
              rel="noopener noreferrer"
              className="flex items-center gap-2 px-6 py-3 bg-gradient-to-r from-purple-500 to-pink-600 rounded-full hover:scale-110 transition-transform duration-300 shadow-lg hover:shadow-purple-500/50"
            >
              <ExternalLink className="w-5 h-5" />
              Portfolio
            </a>
            <a 
              href="https://drive.google.com/file/d/18Lch5OcZz8NDsOd5LFMMX3mIN7hCuJMx/view?usp=sharing"
              target="_blank"
              rel="noopener noreferrer"
              className="flex items-center gap-2 px-6 py-3 bg-gradient-to-r from-amber-500 to-orange-600 rounded-full hover:scale-110 transition-transform duration-300 shadow-lg hover:shadow-amber-500/50"
            >
              <Award className="w-5 h-5" />
              Resume
            </a>
          </div>
        </div>

        {/* Stats Cards */}
        <div className="grid grid-cols-2 md:grid-cols-4 gap-6 mt-16">
          {projects.map((project, index) => {
            const IconComponent = project.icon;
            return (
              <div
                key={index}
                className="group relative overflow-hidden rounded-2xl cursor-pointer"
                style={{ animationDelay: `${index * 100}ms` }}
              >
                <div className={`${project.color} p-6 h-full transition-transform duration-300 group-hover:scale-105`}>
                  <div className="flex flex-col items-center text-center">
                    <IconComponent className="w-12 h-12 mb-3 group-hover:rotate-12 transition-transform duration-300" />
                    <p className="text-4xl font-bold mb-2">{project.count}</p>
                    <p className="text-sm opacity-90">{project.name}</p>
                  </div>
                </div>
                <div className="absolute inset-0 bg-white opacity-0 group-hover:opacity-10 transition-opacity duration-300"></div>
              </div>
            );
          })}
        </div>

        {/* Skills Section */}
        <div className="mt-20">
          <h2 className="text-4xl font-bold text-center mb-12 bg-gradient-to-r from-cyan-400 to-purple-400 bg-clip-text text-transparent">
            🛠️ Tech Arsenal
          </h2>
          <div className="grid grid-cols-2 md:grid-cols-4 gap-6">
            {skills.map((skill, index) => (
              <div
                key={index}
                className="group relative overflow-hidden rounded-xl bg-slate-800/50 backdrop-blur-sm border border-slate-700 hover:border-cyan-400 transition-all duration-300 cursor-pointer"
                style={{ animationDelay: `${index * 50}ms` }}
              >
                <div className="p-6 text-center">
                  <div className="text-4xl mb-3 group-hover:scale-125 transition-transform duration-300">
                    {skill.icon}
                  </div>
                  <p className={`font-semibold bg-gradient-to-r ${skill.color} bg-clip-text text-transparent`}>
                    {skill.name}
                  </p>
                </div>
                <div className={`absolute inset-0 bg-gradient-to-r ${skill.color} opacity-0 group-hover:opacity-10 transition-opacity duration-300`}></div>
              </div>
            ))}
          </div>
        </div>

        {/* Coding Platforms */}
        <div className="mt-20">
          <h2 className="text-4xl font-bold text-center mb-12 bg-gradient-to-r from-green-400 to-cyan-400 bg-clip-text text-transparent">
            🚀 Coding Platforms
          </h2>
          <div className="flex flex-wrap justify-center gap-6">
            {codingPlatforms.map((platform, index) => (
              <a
                key={index}
                href={platform.url}
                target="_blank"
                rel="noopener noreferrer"
                className={`${platform.color} ${platform.hoverColor} px-8 py-4 rounded-xl font-semibold text-lg transition-all duration-300 transform hover:scale-110 hover:shadow-2xl flex items-center gap-2`}
              >
                <Terminal className="w-5 h-5" />
                {platform.name}
                <ChevronRight className="w-5 h-5" />
              </a>
            ))}
          </div>
        </div>

        {/* GitHub Stats */}
        <div className="mt-20">
          <h2 className="text-4xl font-bold text-center mb-12 bg-gradient-to-r from-pink-400 to-purple-400 bg-clip-text text-transparent">
            📊 GitHub Analytics
          </h2>
          <div className="grid md:grid-cols-2 gap-8">
            <div className="bg-slate-800/50 backdrop-blur-sm rounded-2xl p-4 border border-slate-700 hover:border-purple-400 transition-all duration-300 hover:scale-105">
              <img 
                src="https://github-readme-stats.vercel.app/api?username=Shubhamchaudhari1807&show_icons=true&theme=radical&hide_border=true" 
                alt="GitHub Stats"
                className="w-full rounded-lg"
              />
            </div>
            <div className="bg-slate-800/50 backdrop-blur-sm rounded-2xl p-4 border border-slate-700 hover:border-purple-400 transition-all duration-300 hover:scale-105">
              <img 
                src="https://github-readme-stats.vercel.app/api/top-langs/?username=Shubhamchaudhari1807&layout=compact&theme=radical&hide_border=true" 
                alt="Top Languages"
                className="w-full rounded-lg"
              />
            </div>
          </div>
          
          <div className="mt-8 bg-slate-800/50 backdrop-blur-sm rounded-2xl p-4 border border-slate-700 hover:border-purple-400 transition-all duration-300 hover:scale-105">
            <img 
              src="https://streak-stats.demolab.com?user=Shubhamchaudhari1807&theme=radical&hide_border=true" 
              alt="GitHub Streak"
              className="w-full rounded-lg"
            />
          </div>

          <div className="mt-8 bg-slate-800/50 backdrop-blur-sm rounded-2xl p-4 border border-slate-700 hover:border-purple-400 transition-all duration-300 hover:scale-105">
            <img 
              src="https://github-readme-activity-graph.vercel.app/graph?username=Shubhamchaudhari1807&bg_color=0d1117&color=00cfff&line=00e5ff&point=009dff&area=true&hide_border=true" 
              alt="Activity Graph"
              className="w-full rounded-lg"
            />
          </div>
        </div>

        {/* Achievements */}
        <div className="mt-20 mb-12">
          <h2 className="text-4xl font-bold text-center mb-12 bg-gradient-to-r from-amber-400 to-orange-400 bg-clip-text text-transparent">
            🏆 GitHub Achievements
          </h2>
          <div className="bg-slate-800/50 backdrop-blur-sm rounded-2xl p-4 border border-slate-700 hover:border-amber-400 transition-all duration-300">
            <img 
              src="https://github-profile-trophy.vercel.app/?username=Shubhamchaudhari1807&theme=matrix&no-frame=true&row=2&column=3&margin-w=15&margin-h=15" 
              alt="GitHub Trophies"
              className="w-full rounded-lg"
            />
          </div>
        </div>

        {/* Footer */}
        <div className="text-center mt-20 pb-12">
          <div className="inline-flex items-center gap-2 px-6 py-3 bg-slate-800/50 backdrop-blur-sm rounded-full border border-slate-700">
            <Zap className="w-5 h-5 text-yellow-400 animate-pulse" />
            <span className="text-slate-300">B.Tech Computer Science Graduate 2025</span>
          </div>
          <p className="mt-6 text-slate-400 text-sm">
            Crafted with 💜 by Shubham Chaudhari
          </p>
        </div>
      </div>

      <style jsx>{`
        @keyframes gradient {
          0%, 100% { background-position: 0% 50%; }
          50% { background-position: 100% 50%; }
        }
        .animate-gradient {
          background-size: 200% 200%;
          animation: gradient 3s ease infinite;
        }
      `}</style>
    </div>
  );
}
