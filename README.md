'use client'

import { useState, useEffect } from 'react'
import { motion, AnimatePresence } from 'framer-motion'
import { Button } from "@/components/ui/button"
import { Progress } from "@/components/ui/progress"
import { Badge } from "@/components/ui/badge"
import { Avatar, AvatarFallback, AvatarImage } from "@/components/ui/avatar"
import { Sparkles, Code, Brain, Rocket, Trophy, Heart, Github, Twitter, Mail, Linkedin } from 'lucide-react'

export default function Component() {
  const [xp, setXp] = useState(0)
  const [level, setLevel] = useState(1)
  const [activeProject, setActiveProject] = useState(0)
  const [showHologram, setShowHologram] = useState(false)

  const projects = [
    { name: 'Avisari', description: 'AI-powered personal assistant' },
    { name: 'Nota', description: 'Quantum-encrypted note-taking app' },
    { name: 'Dormeal', description: 'Teleportation-based food delivery service' },
    { name: 'EduConnect', description: 'Holographic classroom experience' },
  ]

  useEffect(() => {
    const xpTimer = setInterval(() => {
      setXp(prevXp => (prevXp + 1) % 100)
    }, 100)

    const levelTimer = setInterval(() => {
      setLevel(prevLevel => prevLevel + 1)
    }, 10000)

    const projectTimer = setInterval(() => {
      setActiveProject(prevProject => (prevProject + 1) % projects.length)
    }, 5000)

    return () => {
      clearInterval(xpTimer)
      clearInterval(levelTimer)
      clearInterval(projectTimer)
    }
  }, [])

  return (
    <div className="min-h-screen bg-black text-neon-blue flex flex-col items-center justify-center p-4">
      <motion.div
        initial={{ opacity: 0 }}
        animate={{ opacity: 1 }}
        transition={{ duration: 2 }}
        className="w-full max-w-4xl"
      >
        <div className="grid grid-cols-1 md:grid-cols-2 gap-8">
          <motion.div
            whileHover={{ scale: 1.05 }}
            className="bg-dark-purple p-8 rounded-lg shadow-neon"
          >
            <div className="flex items-center space-x-4 mb-6">
              <Avatar className="w-20 h-20 ring-2 ring-neon-pink">
                <AvatarImage src="/placeholder.svg?height=80&width=80" alt="Anthony" />
                <AvatarFallback>AC</AvatarFallback>
              </Avatar>
              <div>
                <h1 className="text-3xl font-bold text-neon-pink">Anthony Campos</h1>
                <p className="text-neon-green">Level {level} Code Wizard</p>
              </div>
            </div>

            <motion.div
              animate={{ width: `${xp}%` }}
              className="h-2 bg-neon-green mb-4 rounded-full"
            />

            <div className="flex justify-between mb-6">
              <Badge variant="outline" className="text-xl border-neon-blue">
                <Sparkles className="w-4 h-4 mr-2" />
                {xp}/100 XP
              </Badge>
              <Badge variant="outline" className="text-xl border-neon-pink">
                <Rocket className="w-4 h-4 mr-2" />
                Cyberpunk Coder
              </Badge>
            </div>

            <motion.div
              whileHover={{ scale: 1.05 }}
              className="bg-dark-blue p-4 rounded-lg mb-6"
            >
              <h2 className="font-bold flex items-center mb-2 text-neon-yellow">
                <Code className="w-5 h-5 mr-2" />
                Current Quest
              </h2>
              <p>Integrating LLMs into police bodycams for superhuman law enforcement!</p>
            </motion.div>

            <div className="mb-6">
              <h2 className="font-bold flex items-center mb-2 text-neon-orange">
                <Brain className="w-5 h-5 mr-2" />
                Neural Network
              </h2>
              {['Python', 'React', 'TypeScript', 'Next.js', 'AWS'].map((skill, index) => (
                <motion.div
                  key={skill}
                  initial={{ width: 0 }}
                  animate={{ width: '100%' }}
                  transition={{ duration: 1, delay: index * 0.2 }}
                  className="h-2 bg-neon-blue mb-2 rounded-full"
                />
              ))}
            </div>
          </motion.div>

          <motion.div
            whileHover={{ scale: 1.05 }}
            className="bg-dark-purple p-8 rounded-lg shadow-neon"
          >
            <h2 className="font-bold flex items-center mb-4 text-neon-yellow text-2xl">
              <Trophy className="w-6 h-6 mr-2" />
              Cybernetic Achievements
            </h2>
            <ul className="space-y-4">
              <motion.li
                whileHover={{ scale: 1.1 }}
                className="bg-dark-blue p-3 rounded-lg flex items-center"
              >
                <span className="text-2xl mr-2">🧠</span>
                AI Mastermind
              </motion.li>
              <motion.li
                whileHover={{ scale: 1.1 }}
                className="bg-dark-blue p-3 rounded-lg flex items-center"
              >
                <span className="text-2xl mr-2">🚀</span>
                Quantum Code Deployer
              </motion.li>
              <motion.li
                whileHover={{ scale: 1.1 }}
                className="bg-dark-blue p-3 rounded-lg flex items-center"
              >
                <span className="text-2xl mr-2">🌐</span>
                Neurolink Navigator
              </motion.li>
            </ul>

            <motion.div
              className="mt-8 p-4 bg-dark-blue rounded-lg"
              animate={{ 
                boxShadow: ['0 0 0 0 rgba(0, 255, 255, 0.7)', '0 0 0 10px rgba(0, 255, 255, 0)'],
              }}
              transition={{ 
                repeat: Infinity, 
                duration: 2
              }}
            >
              <h3 className="text-neon-green text-xl mb-2">Featured Project:</h3>
              <AnimatePresence mode="wait">
                <motion.div
                  key={activeProject}
                  initial={{ opacity: 0, y: 20 }}
                  animate={{ opacity: 1, y: 0 }}
                  exit={{ opacity: 0, y: -20 }}
                  transition={{ duration: 0.5 }}
                >
                  <h4 className="text-neon-pink text-lg">{projects[activeProject].name}</h4>
                  <p>{projects[activeProject].description}</p>
                </motion.div>
              </AnimatePresence>
            </motion.div>
          </motion.div>
        </div>

        <motion.div 
          className="mt-8 flex justify-center space-x-6"
          initial={{ opacity: 0, y: 20 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ delay: 1 }}
        >
          <motion.a 
            href="https://github.com/yourusername" 
            whileHover={{ scale: 1.2, rotate: 360 }}
            className="text-neon-blue hover:text-neon-pink"
          >
            <Github size={32} />
          </motion.a>
          <motion.a 
            href="mailto:anthonyrubencampos@gmail.com" 
            whileHover={{ scale: 1.2, rotate: 360 }}
            className="text-neon-blue hover:text-neon-pink"
          >
            <Mail size={32} />
          </motion.a>
          <motion.a 
            href="https://twitter.com/heyanthonny" 
            whileHover={{ scale: 1.2, rotate: 360 }}
            className="text-neon-blue hover:text-neon-pink"
          >
            <Twitter size={32} />
          </motion.a>
          <motion.a 
            href="https://www.linkedin.com/in/yourusername" 
            whileHover={{ scale: 1.2, rotate: 360 }}
            className="text-neon-blue hover:text-neon-pink"
          >
            <Linkedin size={32} />
          </motion.a>
        </motion.div>

        <motion.div 
          className="mt-8 text-center"
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
          transition={{ delay: 1.5 }}
        >
          <Button 
            onClick={() => setShowHologram(!showHologram)}
            className="bg-neon-purple hover:bg-neon-pink text-white"
          >
            Toggle Holographic Message
          </Button>
        </motion.div>

        <AnimatePresence>
          {showHologram && (
            <motion.div
              initial={{ opacity: 0, scale: 0 }}
              animate={{ opacity: 1, scale: 1 }}
              exit={{ opacity: 0, scale: 0 }}
              className="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50"
              onClick={() => setShowHologram(false)}
            >
              <motion.div 
                className="bg-dark-purple p-8 rounded-lg text-neon-green text-center"
                animate={{ 
                  boxShadow: ['0 0 0 0 rgba(0, 255, 255, 0.7)', '0 0 0 20px rgba(0, 255, 255, 0)'],
                }}
                transition={{ 
                  repeat: Infinity, 
                  duration: 2
                }}
              >
                <h2 className="text-2xl mb-4">Greetings, fellow coder!</h2>
                <p>Welcome to my cybernetic realm of innovation.</p>
                <p>Let's shape the future, one line of code at a time.</p>
              </motion.div>
            </motion.div>
          )}
        </AnimatePresence>
      </motion.div>
    </div>
  )
}
