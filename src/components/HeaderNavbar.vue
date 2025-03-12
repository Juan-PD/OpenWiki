<script setup>
import openwiki_logo from '@/assets/img/openwiki.png'
import { ref } from 'vue'

const mobileMenuOpen = ref(false)

function toggleMobileMenu() {
  mobileMenuOpen.value = !mobileMenuOpen.value
}
</script>

<template>
  <header>
    <!-- Navigation Bar -->
    <nav class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 bg-white border-b border-gray-200">
      <div class="flex justify-between h-16">
        <!-- Logo and primary navigation -->
        <div class="flex items-center">
          <div class="flex-shrink-0 flex items-center">
            <router-link to="/" class="flex items-center">
              <img :src="openwiki_logo" class="h-8 w-auto" alt="Logo de OpenWiki" />
              <span class="ml-2 text-xl font-bold text-[#2c5f2d]">OpenWiki</span>
            </router-link>
          </div>
          <div class="hidden sm:ml-6 sm:flex sm:space-x-8">
            <!-- Navigation links remain unchanged -->
            <router-link
              to="/"
              class="border-transparent text-gray-500 hover:border-[#2c5f2d] hover:text-[#2c5f2d] inline-flex items-center px-1 pt-1 border-b-2 text-sm font-medium"
            >
              Inicio
            </router-link>
            <router-link
              to="/docs"
              class="border-transparent text-gray-500 hover:border-[#2c5f2d] hover:text-[#2c5f2d] inline-flex items-center px-1 pt-1 border-b-2 text-sm font-medium"
            >
              Documentación
            </router-link>
            <router-link
              to="/community"
              class="border-transparent text-gray-500 hover:border-[#2c5f2d] hover:text-[#2c5f2d] inline-flex items-center px-1 pt-1 border-b-2 text-sm font-medium"
            >
              Comunidad
            </router-link>
          </div>
        </div>

        <!-- Search bar - hidden on smallest screens -->
        <div
          class="hidden sm:flex-1 sm:flex sm:items-center sm:justify-center px-2 lg:ml-6 lg:justify-end"
        >
          <div class="max-w-lg w-full lg:max-w-xs">
            <div class="relative">
              <input
                type="text"
                placeholder="Buscar en OpenWiki"
                class="block w-full pl-3 pr-10 py-2 border border-gray-300 rounded-md leading-5 bg-white placeholder-gray-500 focus:outline-none focus:placeholder-gray-400 focus:ring-1 focus:ring-[#97bc62] focus:border-[#97bc62] sm:text-sm"
                aria-label="Buscar en el sitio"
              />
              <button class="absolute inset-y-0 right-0 pr-3 flex items-center">
                <svg
                  class="h-5 w-5 text-gray-400"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                  aria-hidden="true"
                >
                  <path
                    fill-rule="evenodd"
                    d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
                    clip-rule="evenodd"
                  />
                </svg>
              </button>
            </div>
          </div>
        </div>

        <!-- User navigation and mobile menu button -->
        <div class="flex items-center">
          <!-- Desktop user navigation -->
          <div class="hidden md:ml-4 md:flex md:items-center md:space-x-4">
            <router-link
              to="/login"
              class="text-gray-500 hover:text-[#2c5f2d] px-3 py-2 rounded-md text-sm font-medium"
            >
              Iniciar sesión
            </router-link>
            <router-link
              to="/register"
              class="bg-[#2c5f2d] text-white hover:bg-[#1e3f1f] px-3 py-2 rounded-md text-sm font-medium"
            >
              Registrarse
            </router-link>
          </div>

          <!-- Mobile menu button -->
          <div class="flex items-center sm:ml-6 md:hidden">
            <button
              @click="toggleMobileMenu"
              type="button"
              class="inline-flex items-center justify-center p-2 rounded-md text-gray-500 hover:text-[#2c5f2d] hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-[#97bc62]"
              aria-controls="mobile-menu"
              :aria-expanded="mobileMenuOpen"
            >
              <span class="sr-only">Abrir menú principal</span>
              <!-- Icon when menu is closed -->
              <svg
                :class="{ hidden: mobileMenuOpen, block: !mobileMenuOpen }"
                class="h-6 w-6"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                aria-hidden="true"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M4 6h16M4 12h16M4 18h16"
                />
              </svg>
              <!-- Icon when menu is open -->
              <svg
                :class="{ block: mobileMenuOpen, hidden: !mobileMenuOpen }"
                class="h-6 w-6"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                aria-hidden="true"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M6 18L18 6M6 6l12 12"
                />
              </svg>
            </button>
          </div>
        </div>
      </div>

      <!-- Mobile menu, show/hide based on menu state -->
      <div
        id="mobile-menu"
        :class="{ block: mobileMenuOpen, hidden: !mobileMenuOpen }"
        class="md:hidden overflow-hidden"
        :style="{ 
          maxHeight: mobileMenuOpen ? '500px' : '0',
          opacity: mobileMenuOpen ? '1' : '0',
          transform: mobileMenuOpen ? 'translateY(0)' : 'translateY(-10px)'
        }"
      >
        <div class="pt-2 pb-3 space-y-1">
          <router-link
            to="/"
            class="text-gray-500 hover:bg-gray-50 hover:text-[#2c5f2d] block px-3 py-2 rounded-md text-base font-medium"
            active-class="bg-[#2c5f2d]/10 text-[#2c5f2d]"
          >
            Inicio
          </router-link>
          <router-link
            to="/docs"
            class="text-gray-500 hover:bg-gray-50 hover:text-[#2c5f2d] block px-3 py-2 rounded-md text-base font-medium"
            active-class="bg-[#2c5f2d]/10 text-[#2c5f2d]"
          >
            Documentación
          </router-link>
          <router-link
            to="/community"
            class="text-gray-500 hover:bg-gray-50 hover:text-[#2c5f2d] block px-3 py-2 rounded-md text-base font-medium"
            active-class="bg-[#2c5f2d]/10 text-[#2c5f2d]"
          >
            Comunidad
          </router-link>
        </div>

        <!-- Mobile search -->
        <div class="pt-2 pb-3 px-3">
          <div class="relative">
            <input
              type="text"
              placeholder="Buscar en OpenWiki"
              class="block w-full pl-3 pr-10 py-2 border border-gray-300 rounded-md leading-5 bg-white placeholder-gray-500 focus:outline-none focus:placeholder-gray-400 focus:ring-1 focus:ring-[#97bc62] focus:border-[#97bc62] text-sm"
              aria-label="Buscar en el sitio"
            />
            <button class="absolute inset-y-0 right-0 pr-3 flex items-center">
              <svg
                class="h-5 w-5 text-gray-400"
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 20 20"
                fill="currentColor"
                aria-hidden="true"
              >
                <path
                  fill-rule="evenodd"
                  d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
                  clip-rule="evenodd"
                />
              </svg>
            </button>
          </div>
        </div>

        <!-- Mobile user navigation -->
        <div class="pt-4 pb-3 border-t border-gray-200">
          <div class="flex items-center px-3 space-x-3">
            <router-link
              to="/login"
              class="block text-gray-500 hover:text-[#2c5f2d] px-3 py-2 rounded-md text-base font-medium"
            >
              Iniciar sesión
            </router-link>
            <router-link
              to="/register"
              class="block bg-[#2c5f2d] text-white hover:bg-[#1e3f1f] px-3 py-2 rounded-md text-base font-medium"
            >
              Registrarse
            </router-link>
          </div>
        </div>
      </div>
    </nav>

    <!-- Hero Section - Made more responsive -->
    <div class="bg-gradient-to-r from-[#2c5f2d] to-[#1e3f1f] text-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12 md:py-16 lg:py-24">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
          <div>
            <h1
              class="text-3xl sm:text-4xl md:text-5xl font-bold tracking-tight mb-4 text-center md:text-left"
            >
              OpenWiki: Preservando Lenguas Indígenas
            </h1>
            <p class="text-base sm:text-lg md:text-xl mb-8 text-gray-100 text-center md:text-left">
              Una plataforma colaborativa para documentar, preservar y revitalizar las lenguas
              indígenas de México.
            </p>
            <div class="flex flex-col sm:flex-row gap-4 justify-center md:justify-start">
              <router-link
                to="/explore"
                class="inline-flex items-center justify-center px-6 py-3 border border-transparent text-base font-medium rounded-md text-[#2c5f2d] bg-white hover:bg-gray-100 transition duration-300 w-full sm:w-auto"
              >
                Explorar lenguas
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-5 w-5 ml-2"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                >
                  <path
                    fill-rule="evenodd"
                    d="M10.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L12.586 11H5a1 1 0 110-2h7.586l-2.293-2.293a1 1 0 010-1.414z"
                    clip-rule="evenodd"
                  />
                </svg>
              </router-link>
              <router-link
                to="/contribute"
                class="inline-flex items-center justify-center px-6 py-3 border border-[#97bc62] text-base font-medium rounded-md text-white hover:bg-[#97bc62]/30 transition duration-300 w-full sm:w-auto"
              >
                Contribuir
              </router-link>
            </div>
          </div>

          <!-- Stats cards - now visible on smaller screens but in a different layout -->
          <div class="mt-10 md:mt-0">
            <div class="relative">
              <!-- Decorative elements - hidden on small screens -->
              <div
                class="absolute -top-6 -left-6 w-32 h-32 bg-[#97bc62] rounded-full opacity-20 hidden md:block"
              ></div>
              <div
                class="absolute -bottom-6 -right-6 w-32 h-32 bg-[#97bc62] rounded-full opacity-20 hidden md:block"
              ></div>

              <!-- Main stats container -->
              <div class="relative z-10 bg-[#1e3f1f] p-4 md:p-6 rounded-lg shadow-xl">
                <div class="grid grid-cols-2 gap-3 md:gap-4">
                  <div class="bg-[#97bc62]/20 p-3 md:p-4 rounded-lg text-center">
                    <h3 class="text-xl md:text-2xl font-bold mb-1 md:mb-2">68</h3>
                    <p class="text-xs md:text-sm text-gray-100">Lenguas indígenas en México</p>
                  </div>
                  <div class="bg-[#97bc62]/20 p-3 md:p-4 rounded-lg text-center">
                    <h3 class="text-xl md:text-2xl font-bold mb-1 md:mb-2">364</h3>
                    <p class="text-xs md:text-sm text-gray-100">Variantes lingüísticas</p>
                  </div>
                  <div class="bg-[#97bc62]/20 p-3 md:p-4 rounded-lg text-center">
                    <h3 class="text-xl md:text-2xl font-bold mb-1 md:mb-2">25+</h3>
                    <p class="text-xs md:text-sm text-gray-100">Millones de hablantes</p>
                  </div>
                  <div class="bg-[#97bc62]/20 p-3 md:p-4 rounded-lg text-center">
                    <h3 class="text-xl md:text-2xl font-bold mb-1 md:mb-2">7.5M+</h3>
                    <p class="text-xs md:text-sm text-gray-100">Hablantes actuales</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Wave decoration - improved positioning -->
      <div class="relative h-16">
        <svg
          class="absolute bottom-0 left-0 w-full h-full text-white fill-current"
          viewBox="0 0 1440 120"
          preserveAspectRatio="none"
        >
          <path
            d="M0,64L80,69.3C160,75,320,85,480,80C640,75,800,53,960,48C1120,43,1280,53,1360,58.7L1440,64L1440,120L1360,120C1280,120,1120,120,960,120C800,120,640,120,480,120C320,120,160,120,80,120L0,120Z"
          ></path>
        </svg>
      </div>
    </div>
  </header>
</template>

<style scoped>
.router-link-active {
  color: #2c5f2d;
  border-bottom-color: #2c5f2d;
}

/* Responsive transitions */
@media (max-width: 640px) {
  .hero-text {
    text-align: center;
  }
}

/* Improved mobile menu animation */
#mobile-menu {
  transition: all 0.15s cubic-bezier(0.17, 0.67, 0.83, 0.67);
  transform-origin: top;
  will-change: transform, opacity, max-height;
  pointer-events: none;
}

#mobile-menu.hidden {
  opacity: 0;
  visibility: hidden;
}

#mobile-menu.block {
  opacity: 1;
  visibility: visible;
  pointer-events: auto;
}
</style>
