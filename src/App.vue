<template>
  <div id="app" :class="{ dark: isDarkMode }">
    <header class="fade-in">
      <img src="/src/assets/logo.svg" alt="FoxHost Logo" class="logo" />
      <h1>FoxHost</h1>
      <button class="dark-toggle" @click="toggleDarkMode">
        {{ isDarkMode ? '☀️ Light Mode' : '🌙 Dark Mode' }}
      </button>
    </header>

    <section class="hero fade-up">
      <div class="hero-glow"></div>
      <h2>Welcome to Meow Mods SMP</h2>
      <p>
        A cozy and friendly modded Minecraft server hosted and maintained by FoxHost, featuring the
        custom Meow Mods modpack.
      </p>
      <button
        onclick="window.location.href='https://modrinth.com/modpack/meow-mods';"
        class="cta-button"
      >
        Join Our Community
      </button>
    </section>

    <section class="features fade-up">
      <div class="feature" v-for="(feature, index) in features" :key="index">
        <h3>{{ feature.title }}</h3>
        <p>{{ feature.description }}</p>
      </div>
    </section>

    <section class="server-info fade-up">
      <h2>Server IP</h2>
      <p><strong>meow.foxhost.us.to</strong></p>
      <p>Version: 1.20.1 Forge | Meow Mods Modpack</p>
    </section>

    <section class="about fade-up">
      <h2>About Meow Mods</h2>
      <p>
        Meow Mods is a custom Minecraft modpack designed for our small SMP community. Hosted on
        FoxHost servers, it blends performance and fun with unique mods and a supportive
        environment. Whether you're automating factories or casting spells, there's something for
        everyone.
      </p>
    </section>

    <footer class="fade-in">&copy; 2025 FoxHost / Meow Mods. All rights reserved.</footer>
  </div>
</template>

<script>
export default {
  name: 'FoxHostApp',
  data() {
    return {
      features: [
        {
          title: 'Modded Experience',
          description:
            'Dive into a hand-picked collection of mods that enhance your gameplay with tech, magic, and exploration.',
        },
        {
          title: 'Small & Friendly',
          description:
            'A small, tight-knit community of around 10 active players. Perfect for those who enjoy chill vibes.',
        },
        {
          title: 'Stable Hosting',
          description:
            'FoxHost ensures your modded adventures run smoothly with reliable uptime and fast support.',
        },
      ],
      isDarkMode: true,
    }
  },
  mounted() {
    const elements = document.querySelectorAll('.fade-up, .fade-in')
    elements.forEach((el) => el.classList.add('visible'))
    const savedTheme = localStorage.getItem('foxhost-dark')
    this.isDarkMode = savedTheme === null ? true : savedTheme === 'true'
  },
  methods: {
    toggleDarkMode() {
      this.isDarkMode = !this.isDarkMode
      localStorage.setItem('foxhost-dark', this.isDarkMode)
    },
  },
}
</script>

<style scoped>
body,
#app {
  margin: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: linear-gradient(to bottom right, #0091ea, #00c8ff);
  color: white;
}
.logo {
  filter: invert();
}
body .dark {
  background: linear-gradient(to bottom right, #000000, #000000) !important;
}
.dark {
  background: #0a0a0a;
  color: #e0e0e0;
}
.dark .features {
  background-color: #000000 !important;
}
.dark .feature {
  background: radial-gradient(circle, rgba(0, 200, 255, 0.3) 0%, transparent 55%);
  background-size: 50%;
  background-position: center;
  background-repeat: no-repeat;
  transition-property: all;
  transition-duration: 0.3s;
}
.dark .feature:hover {
  background: radial-gradient(circle, rgba(0, 200, 255, 0.3) 0%, transparent 55%);
  background-size: 100%;
  background-position: center;
  background-repeat: no-repeat;
  transition-property: all;
  transition-duration: 0.3s;
}
.dark footer {
  background-color: rgba(255, 255, 255, 0.05);
}
.dark .cta-button {
  background-color: #000;
  color: #00c8ff;
}
.dark .cta-button:hover {
  background-color: #333;
}
.dark-toggle {
  margin-left: auto;
  background: none;
  border: 1px solid currentColor;
  padding: 0.4rem 1rem;
  border-radius: 5px;
  cursor: pointer;
  color: inherit;
  font-size: 0.9rem;
  margin-left: auto;
  margin-right: 0.5rem;
}
.dark .hero h2 {
  font-size: 3rem;
  margin-bottom: 1rem;
  background: linear-gradient(35deg, #0091ea 0%, #00c8ff 100%);
  color: transparent;
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}
header {
  display: flex;
  align-items: center;
  padding: 1rem 2rem;
  background-color: rgba(0, 0, 0, 0);
}
header img {
  height: 40px;
  margin-right: 10px;
}
header h1 {
  font-size: 1.8rem;
  margin: 0;
}
.hero {
  text-align: center;
  padding: 6rem 2rem 4rem;
  position: relative;
} /*
.hero-glow {
  position: absolute;
  top: 50%;
  left: 40%;
  transform: translateX(-50%);
  width: 25%;
  height: 33%;
  background: radial-gradient(circle, rgba(0, 200, 255, 0.3) 0%, transparent 70%);
  z-index: 0;
  pointer-events: none;
  filter: blur(500px);
  transition-property: all;
  transition-duration: 0.3s;
}*/
.hero-glow {
  position: absolute;
  top: 0;
  left: 10%; /*
  transform: translateX(-50%);*/
  width: 80%;
  height: 100%;
  background: radial-gradient(circle, rgba(0, 200, 255, 0.3) 0%, transparent 70%);
  z-index: 0;
  pointer-events: none;
  filter: blur(500px);
  opacity: 0;
  transition-property: all;
  transition-duration: 0.3s;
}

.dark .hero-glow {
  position: absolute;
  top: 0;
  left: 10%; /*
  transform: translateX(-50%);*/
  width: 80%;
  height: 100%;
  background: radial-gradient(circle, rgba(0, 200, 255, 0.3) 0%, transparent 70%);
  z-index: 0;
  pointer-events: none;
  filter: blur(50px);
  opacity: 1;
  animation-timing-function: ease-in-out;
  animation: hero-glow-breath 5s infinite;
}
@keyframes hero-glow-breath {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(0.8);
  }
  100% {
    transform: scale(1);
  }
}
.hero h2,
.hero p,
.cta-button {
  position: relative;
  z-index: 1;
}
.hero h2 {
  font-size: 3rem;
  margin-bottom: 1rem;
}
.hero p {
  font-size: 1.2rem;
  max-width: 600px;
  margin: 0 auto;
}
.cta-button {
  margin-top: 2rem;
  padding: 1rem 2rem;
  font-size: 1rem;
  background-color: white;
  color: #0091ea;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-weight: bold;
  transition:
    background 0.3s ease,
    transform 0.3s ease;
}
.cta-button:hover {
  background-color: #e0f7ff;
  transform: scale(1.05);
}
.features {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  padding: 4rem 2rem;
  background-color: rgba(255, 255, 255, 0.05);
}
.feature {
  max-width: 300px;
  margin: 1rem;
  padding: 2rem;
  background-color: rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  text-align: center;
  transition: transform 0.3s ease;
}
.feature:hover {
  transform: translateY(-5px);
}
.feature h3 {
  margin-bottom: 1rem;
  font-size: 1.5rem;
}
.feature p {
  font-size: 1rem;
}
.about {
  padding: 4rem 2rem;
  text-align: center;
}
.about h2 {
  font-size: 2rem;
  margin-bottom: 1rem;
}
.about p {
  font-size: 1.1rem;
  max-width: 800px;
  margin: 0 auto;
}
.server-info {
  text-align: center;
  padding: 4rem 2rem;
}
.server-info h2 {
  font-size: 2rem;
  margin-bottom: 1rem;
}
.server-info p {
  font-size: 1.2rem;
}
footer {
  text-align: center;
  padding: 2rem;
  font-size: 0.9rem;
  background-color: rgba(0, 0, 0, 0.1);
}
.fade-in,
.fade-up {
  opacity: 0;
  transform: translateY(20px);
  transition:
    opacity 0.8s ease,
    transform 0.8s ease;
}
.fade-in.visible,
.fade-up.visible {
  opacity: 1;
  transform: none;
}
</style>
