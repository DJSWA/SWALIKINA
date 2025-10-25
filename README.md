# SWALIKINA
SWALIKINAPROUGANDAN 

/*
SWALIKINA PRO — Website Starter (React / Next.js + Tailwind)
*/

import React, { useState, useRef } from 'react'

const sampleMedia = {
  music: [
    { id: 1, title: 'Nightfall', artist: 'Aria Lane', cover: '/placeholder-music1.jpg', src: '/sample-audio.mp3' },
    { id: 2, title: 'Pulse', artist: 'DJ Kito', cover: '/placeholder-music2.jpg', src: '/sample-audio.mp3' },
    { id: 3, title: 'Echoes', artist: 'Luna Rae', cover: '/placeholder-music3.jpg', src: '/sample-audio.mp3' }
  ],
  films: [
    { id: 1, title: 'The Watcher', poster: '/placeholder-film1.jpg', trailer: '/sample-video.mp4' },
    { id: 2, title: 'The Last Stand', poster: '/placeholder-film2.jpg', trailer: '/sample-video.mp4' },
    { id: 3, title: 'Midnight Road', poster: '/placeholder-film3.jpg', trailer: '/sample-video.mp4' }
  ]
}

export default function SwalikinaProStarter(){
  const [playing, setPlaying] = useState(null)
  const audioRef = useRef(null)
  const videoRef = useRef(null)

  function playMusic(item){
    console.log('playMusic called with item:', item)
    if (audioRef.current){
      console.log('audioRef is available')
      if (playing === item.id){
        console.log('Pausing currently playing item:', item.id)
        audioRef.current.pause()
        setPlaying(null)
      } else {
        console.log('Playing new item:', item.id)
        audioRef.current.src = item.src
        audioRef.current.play().then(()=>{
          console.log('Audio playback started successfully')
        }).catch(err=>{
          console.error('Audio playback error:', err)
        })
        setPlaying(item.id)
      }
    } else {
      console.warn('audioRef not found')
    }
  }

  function playTrailer(trailer){
    console.log('playTrailer called with trailer:', trailer)
    if (videoRef.current){
      console.log('videoRef is available')
      videoRef.current.src = trailer
      videoRef.current.play().then(()=>{
        console.log('Video playback started successfully')
      }).catch(err=>{
        console.error('Video playback error:', err)
      })
    } else {
      console.warn('videoRef not found')
    }
  }

  console.log('Rendering SwalikinaProStarter component')

  return (
    <div className="min-h-screen bg-[#0b0b0b] text-gray-100 antialiased">
      <header className="max-w-7xl mx-auto px-6 py-6 flex items-center justify-between">
        <div className="flex items-center gap-3">
          <div className="w-10 h-10 bg-gradient-to-br from-yellow-500 to-yellow-600 rounded flex items-center justify-center"> 
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none"><path d="M9 7v10a3 3 0 1 0 2 0V6l8-2v10" stroke="black" strokeWidth="1.2"/></svg>
          </div>
          <div>
            <div className="text-xl font-bold tracking-wider">SWALIKINA PRO</div>
            <div className="text-xs text-gray-300">MUSIC AND FILMZ</div>
          </div>
        </div>
        <nav className="hidden md:flex gap-6 items-center text-sm text-gray-300">
          <a className="hover:text-white" href="#">Home</a>
          <a className="hover:text-white" href="#music">Music</a>
          <a className="hover:text-white" href="#filmz">Filmz</a>
          <a className="hover:text-white" href="#artists">Artists</a>
          <button className="ml-2 px-4 py-2 border border-gray-700 rounded">Login</button>
        </nav>
      </header>

      <main className="max-w-7xl mx-auto px-6">
        <section className="relative bg-[url('/hero-placeholder.jpg')] bg-cover bg-center rounded-2xl overflow-hidden p-8 flex flex-col md:flex-row items-center gap-8" style={{minHeight: '360px'}}>
          <div className="backdrop-brightness-75 p-6 rounded-md w-full md:w-2/3">
            <h1 className="text-4xl md:text-5xl font-extrabold leading-tight">Stream. Discover. Create.</h1>
            <p className="text-gray-300 mt-4 max-w-xl">SWALIKINA PRO — curated music and films for creators and listeners. Explore new releases and independent work from around the world.</p>
            <div className="mt-6 flex gap-3">
              <a href="#music" className="px-5 py-3 bg-yellow-500 text-black rounded-md font-semibold">Explore Music</a>
              <a href="#filmz" className="px-5 py-3 border border-yellow-600 rounded-md text-yellow-300 font-semibold">Explore Filmz</a>
            </div>
          </div>
          <div className="hidden md:block flex-1">
            <div className="w-full h-56 bg-gradient-to-tr from-black/40 to-white/5 rounded-lg flex items-center justify-center text-sm text-gray-400">Featured Visual</div>
          </div>
        </section>

        <section id="music" className="mt-10">
          <div className="flex items-center justify-between">
            <h2 className="text-2xl font-semibold">Trending Music</h2>
            <a href="#" className="text-sm text-gray-400">See all</a>
          </div>
          <div className="mt-4 grid grid-cols-2 sm:grid-cols-3 md:grid-cols-6 gap-4">
            {sampleMedia.music.map(item => (
              <div key={item.id} className="bg-[#0f0f0f] rounded-lg p-3 cursor-pointer hover:scale-105 transition" onClick={()=>{console.log('Clicked on music item:', item); playMusic(item)}}>
                <div className="w-full h-32 bg-gray-800 rounded overflow-hidden flex items-center justify-center">
                  <img src={item.cover} alt={item.title} className="w-full h-full object-cover"/>
                </div>
                <div className="mt-2">
                  <div className="text-sm font-medium">{item.title}</div>
                  <div className="text-xs text-gray-400">{item.artist}</div>
                </div>
              </div>
            ))}
          </div>
        </section>

        <section id="filmz" className="mt-10">
          <div className="flex items-center justify-between">
            <h2 className="text-2xl font-semibold">Latest Filmz</h2>
            <a href="#" className="text-sm text-gray-400">See all</a>
          </div>
          <div className="mt-4 grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6">
            {sampleMedia.films.map(f => (
              <div key={f.id} className="bg-[#0f0f0f] rounded-lg overflow-hidden">
                <div className="w-full h-64 bg-gray-800 relative cursor-pointer" onClick={()=>{console.log('Clicked on film:', f); playTrailer(f.trailer)}}>
                  <img src={f.poster} alt={f.title} className="w-full h-full object-cover"/>
                  <div className="absolute inset-0 flex items-center justify-center">
                    <div className="bg-black/40 rounded-full p-3">
                      <svg width="30" height="30" viewBox="0 0 24 24" fill="none"><path d="M8 5v14l11-7L8 5z" fill="#fff"/></svg>
                    </div>
                  </div>
                </div>
                <div className="p-4">
                  <div className="font-semibold">{f.title}</div>
                </div>
              </div>
            ))}
          </div>
        </section>

        <section className="mt-12 mb-24 grid grid-cols-1 md:grid-cols-3 gap-6">
          <div className="p-6 bg-[#0f0f0f] rounded-lg">
            <h3 className="font-semibold">Artist Spotlight</h3>
            <p className="text-sm text-gray-400 mt-2">Monthly feature on an independent artist pushing boundaries.</p>
          </div>
          <div className="p-6 bg-[#0f0f0f] rounded-lg">
            <h3 className="font-semibold">News & Releases</h3>
            <p className="text-sm text-gray-400 mt-2">Announcements, interviews, and behind-the-scenes.</p>
          </div>
          <div className="p-6 bg-[#0f0f0f] rounded-lg">
            <h3 className="font-semibold">About SWALIKINA PRO</h3>
            <p className="text-sm text-gray-400 mt-2">Mission to elevate creators and bring cinematic music experiences to listeners worldwide.</p>
          </div>
        </section>

      </main>

      <audio ref={audioRef} controls className="fixed bottom-4 left-4 w-80 hidden" />
      <video ref={videoRef} controls className="fixed bottom-4 right-4 w-96 hidden" />

      <footer className="border-t border-[#111] mt-12 py-6 text-center text-sm text-gray-500">© {new Date().getFullYear()} SWALIKINA PRO — Music and Filmz</footer>
    </div>
  )
}
