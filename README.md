import { useState } from 'react';
import { Card, CardContent } from '@/components/ui/card';
import { Button } from '@/components/ui/button';
import { LogIn } from 'lucide-react';
import Image from 'next/image';
import { motion } from 'framer-motion';

const articles = [
  { title: 'How to Earn Money Online', thumbnail: '/earn1.jpg', description: 'Best ways to earn money from home.' },
  { title: 'Top 10 Side Hustles', thumbnail: '/earn2.jpg', description: 'Side jobs that pay well in 2025.' },
  { title: 'Affiliate Marketing Guide', thumbnail: '/earn3.jpg', description: 'Step-by-step guide to affiliate marketing.' }
];

export default function HomePage() {
  return (
    <div className="p-6 bg-[#f8f9fa] text-black min-h-screen">
      <header className="flex items-center justify-between py-4 px-6 bg-[#333] text-white shadow-md">
        <h1 className="text-3xl font-bold text-[#FFD700]">Earnify News</h1>
        <Button className="bg-[#FFD700] text-black hover:bg-[#DAA520] flex items-center gap-2">
          <LogIn size={18} /> Login
        </Button>
      </header>
      
      <section className="relative w-full h-[400px] bg-cover bg-center" style={{ backgroundImage: "url('/banner.jpg')" }}>
        <div className="absolute inset-0 bg-gradient-to-b from-transparent to-[#333] flex flex-col justify-end p-10 text-white">
          <h2 className="text-5xl font-bold">Start Earning Online</h2>
          <p className="text-gray-300 max-w-md text-lg">Discover new ways to generate income online.</p>
          <Button className="mt-4 bg-[#FFD700] hover:bg-[#DAA520] text-lg text-black">Read More</Button>
        </div>
      </section>

      <div className="p-6">
        <h2 className="text-4xl font-bold mb-6">Latest Articles</h2>
        <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6">
          {articles.map((article, index) => (
            <motion.div 
              key={index} 
              initial={{ opacity: 0, y: 20 }} 
              animate={{ opacity: 1, y: 0 }} 
              transition={{ duration: 0.5, delay: index * 0.2 }}
            >
              <Card className="bg-white rounded-2xl overflow-hidden shadow-xl hover:shadow-2xl transition-shadow duration-300">
                <Image src={article.thumbnail} alt={article.title} width={300} height={200} className="w-full h-64 object-cover" />
                <CardContent className="p-5">
                  <h2 className="text-2xl font-semibold">{article.title}</h2>
                  <p className="text-gray-600 text-sm mb-4">{article.description}</p>
                  <Button className="w-full flex items-center justify-center gap-2 bg-[#FFD700] hover:bg-[#DAA520] transition-colors text-black">
                    Read More
                  </Button>
                </CardContent>
              </Card>
            </motion.div>
          ))}
        </div>
      </div>
    </div>
  );
}
