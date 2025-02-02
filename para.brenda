"use client"

import { useState, useEffect } from "react"
import { motion, AnimatePresence } from "framer-motion"
import { Heart } from "lucide-react"
import { Input } from "@/components/ui/input"
import { Button } from "@/components/ui/button"
import type React from "react" // Added import for React

export default function ValentinePage() {
  const [name, setName] = useState("")
  const [isValidName, setIsValidName] = useState(false)
  const [showError, setShowError] = useState(false)
  const [showProposal, setShowProposal] = useState(false)
  const [showCelebration, setShowCelebration] = useState(false)
  const [noButtonScale, setNoButtonScale] = useState(1)
  const [currentImageIndex, setCurrentImageIndex] = useState(0)

  const validNames = ["BRENDA", "JOCINEY", "BRENDA JOCINEY"]
  const images = [
    "https://hebbkx1anhila5yf.public.blob.vercel-storage.com/IMG-20241203-WA0025.jpg-cWcx4TAX8jrGgV6IKb6skLM5xOoZcl.jpeg",
    "https://hebbkx1anhila5yf.public.blob.vercel-storage.com/IMG-20250129-WA0010.jpg-B6xbX3gj8jLvs1v4r5hvU0FJBrKuIs.jpeg",
    "https://hebbkx1anhila5yf.public.blob.vercel-storage.com/IMG-20241203-WA0022.jpg-vZ47tbTrjxjGlaptcrs0rv5emBmsGW.jpeg",
    "https://hebbkx1anhila5yf.public.blob.vercel-storage.com/IMG-20250129-WA0006.jpg-RiBrrEvVJ6w2JWNl9BNoHL1YOhoyDo.jpeg",
    "https://hebbkx1anhila5yf.public.blob.vercel-storage.com/IMG-20250129-WA0005.jpg-Z9iy8doc48wI4n1x9uaCMY8hjYTzcx.jpeg",
    "https://hebbkx1anhila5yf.public.blob.vercel-storage.com/IMG-20241203-WA0014.jpg-KPHDU0xbEj1mTaaD2Z3e2zScnoqASe.jpeg",
    "https://hebbkx1anhila5yf.public.blob.vercel-storage.com/IMG-20250201-WA0026.jpg-coSoIJGsdJvAHOcRGPUaYE68pTmaSa.jpeg",
    "https://hebbkx1anhila5yf.public.blob.vercel-storage.com/IMG-20250201-WA0027.jpg-oMcsIpKHhyVCEVwpGPOrRDdqPliRYZ.jpeg",
    "https://hebbkx1anhila5yf.public.blob.vercel-storage.com/IMG-20250201-WA0029.jpg-lBhpLhkIVUu3O1WiALWsIIDuozncpw.jpeg",
  ]

  const handleNameSubmit = (e: React.FormEvent) => {
    e.preventDefault()
    const formattedName = name.toUpperCase()
    if (validNames.includes(formattedName)) {
      setIsValidName(true)
      setShowProposal(true)
      setShowError(false)
    } else {
      setShowError(true)
      setIsValidName(false)
    }
  }

  const handleYesClick = () => {
    setShowProposal(false)
    setShowCelebration(true)
  }

  useEffect(() => {
    if (showCelebration) {
      const interval = setInterval(() => {
        setCurrentImageIndex((prev) => (prev === images.length - 1 ? 0 : prev + 1))
      }, 3000)
      return () => clearInterval(interval)
    }
  }, [showCelebration])

  return (
    <div className="min-h-screen bg-pink-50 flex flex-col items-center justify-center p-4">
      <AnimatePresence>
        {!isValidName && !showError && (
          <motion.div
            initial={{ opacity: 0 }}
            animate={{ opacity: 1 }}
            exit={{ opacity: 0 }}
            className="text-center space-y-6 max-w-md w-full"
          >
            <div className="relative">
              <h1 className="text-3xl font-bold text-pink-600 mb-8">¿Quieres ser mi San Valentín?</h1>
              {[...Array(12)].map((_, i) => (
                <motion.div
                  key={i}
                  className="absolute"
                  animate={{
                    scale: [1, 1.2, 1],
                    opacity: [0.7, 1, 0.7],
                    top: Math.sin(i) * 100,
                    left: Math.cos(i) * 100,
                  }}
                  transition={{
                    repeat: Number.POSITIVE_INFINITY,
                    duration: 2,
                    delay: i * 0.2,
                  }}
                >
                  <Heart className="text-pink-400 h-4 w-4" fill="currentColor" />
                </motion.div>
              ))}
            </div>
            <form onSubmit={handleNameSubmit} className="space-y-4">
              <Input
                type="text"
                value={name}
                onChange={(e) => setName(e.target.value)}
                placeholder="Ingresa tu nombre"
                className="border-pink-300 focus:border-pink-500"
              />
              <Button type="submit" className="w-full bg-pink-500 hover:bg-pink-600">
                Continuar
              </Button>
            </form>
          </motion.div>
        )}

        {showError && (
          <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} exit={{ opacity: 0 }} className="text-center">
            <img
              src="https://hebbkx1anhila5yf.public.blob.vercel-storage.com/perrito-gwS15enEy4rALwBtM6Bc8mJqHRwimu.jpeg"
              alt="Error"
              className="w-64 h-64 object-cover rounded-full mx-auto mb-4"
            />
            <p className="text-red-500 font-semibold">Nombre incorrecto, prueba de nuevo</p>
            <Button onClick={() => setShowError(false)} className="mt-4 bg-pink-500 hover:bg-pink-600">
              Intentar de nuevo
            </Button>
          </motion.div>
        )}

        {showProposal && (
          <motion.div
            initial={{ opacity: 0 }}
            animate={{ opacity: 1 }}
            exit={{ opacity: 0 }}
            className="text-center space-y-8"
          >
            <h2 className="text-3xl font-bold text-pink-600">¿Quieres ser Mi San Valentín?</h2>
            <div className="flex justify-center gap-8">
              <motion.button
                whileHover={{ scale: 1.1 }}
                onClick={handleYesClick}
                className="bg-pink-500 text-white px-8 py-4 rounded-full hover:bg-pink-600 flex items-center gap-2"
              >
                <Heart className="h-6 w-6" fill="currentColor" />
                SI
              </motion.button>
              <motion.button
                style={{ scale: noButtonScale }}
                onClick={() => setNoButtonScale(noButtonScale * 0.8)}
                className="bg-gray-500 text-white px-8 py-4 rounded-lg hover:bg-gray-600"
              >
                NO
              </motion.button>
            </div>
          </motion.div>
        )}

        {showCelebration && (
          <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className="text-center space-y-8 max-w-2xl">
            <motion.h2
              animate={{ scale: [1, 1.1, 1] }}
              transition={{ repeat: Number.POSITIVE_INFINITY, duration: 2 }}
              className="text-3xl font-bold text-pink-600"
            >
              ¡Sabía que dirías que sí, te amo mi amor!
              <br />
              El 14 también es nuestro aniversario, te espero
            </motion.h2>
            <motion.div
              initial={{ opacity: 0 }}
              animate={{ opacity: 1 }}
              transition={{ duration: 0.5 }}
              className="relative"
            >
              <img
                src={images[currentImageIndex] || "/placeholder.svg"}
                alt="Momentos especiales"
                className="w-full max-w-md mx-auto rounded-lg shadow-lg"
              />
              {[...Array(20)].map((_, i) => (
                <motion.div
                  key={i}
                  className="absolute"
                  animate={{
                    scale: [1, 1.2, 1],
                    opacity: [0.7, 1, 0.7],
                    top: Math.random() * 100 - 50 + "%",
                    left: Math.random() * 100 - 50 + "%",
                  }}
                  transition={{
                    repeat: Number.POSITIVE_INFINITY,
                    duration: 2,
                    delay: i * 0.1,
                  }}
                >
                  <Heart className="text-pink-400 h-6 w-6" fill="currentColor" />
                  <span className="absolute text-xs text-pink-600 whitespace-nowrap">Te Amo</span>
                </motion.div>
              ))}
            </motion.div>
          </motion.div>
        )}
      </AnimatePresence>
    </div>
  )
}

