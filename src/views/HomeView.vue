<script setup>
import { ref, computed } from 'vue'
import openwiki_logo from '@/assets/img/openwiki.png'

const languages = [
  "Náhuatl",
  "Maya",
  "Mixteco",
  "Zapoteco",
  "Otomi",
  "Tzeltal",
  "Tzotzil",
  "Mazahua",
  "Chol",
  "Purépecha",
  "Huasteco",
  "Totonaca",
  "Rarámuri",
  "Yaqui",
  "Triqui",
  "Amuzgo",
  "Chichimeca",
  "Tojolabal",
  "Cholulteco",
  "Huichol",
  "Pipil",
  "Ixcateco",
  "Kumiai",
  "Seri",
  "Pame",
  "Cora",
  "Mixe",
  "Zoque",
  "Ayapaneco",
  "Popoloca",
  "Mazateco",
  "Cuicateco",
];

const searchQuery = ref("");

const filteredLanguages = computed(() => {
  return languages.filter(language =>
    language.toLowerCase().includes(searchQuery.value.toLowerCase())
  );
});
</script>

<template>
  <div class="min-h-screen flex flex-col">
    <!-- Header -->
    <header class="bg-[#2c5f2d] py-4 shadow-lg">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex items-center justify-center space-x-4">
          <img :src="openwiki_logo" class="w-20 h-20 drop-shadow-md" alt="Logo de OpenWiki" />
          <h1 class="text-3xl font-bold text-white font-['Chelsea_Market']">OpenWiki</h1>
        </div>
      </div>
    </header>

    <!-- Contenido principal -->
    <main class="flex-grow bg-[#f5f3e7]">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
        <!-- Sección de búsqueda -->
        <div class="mb-16 max-w-2xl mx-auto">
          <div class="relative">
            <input
              v-model="searchQuery"
              type="text"
              placeholder="Buscar lengua indígena..."
              class="w-full px-6 py-4 border-2 border-[#2c5f2d] shadow-lg focus:outline-none focus:ring-4 focus:ring-[#97bc62]/50 text-lg transition-all"
              aria-label="Buscar lengua indígena"
            />
            <svg
              class="absolute right-6 top-4 h-6 w-6 text-gray-500"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"/>
            </svg>
          </div>
        </div>

        <!-- Listado de lenguas -->
        <section class="mb-20">
          <h2 class="text-4xl font-bold text-[#2c5f2d] mb-8 text-center">Lenguas Indígenas de México</h2>
          <p class="text-lg text-gray-700 mb-12 max-w-3xl mx-auto text-center leading-relaxed">
            México alberga una riqueza lingüística única con 68 lenguas indígenas y 364 variantes reconocidas.
            Explora y contribuye a preservar este patrimonio cultural.
          </p>

          <ul class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
            <li
              v-for="(language, index) in filteredLanguages"
              :key="index"
              class="group p-4 bg-white rounded-xl shadow-md hover:shadow-lg transition-shadow duration-300 cursor-pointer border-2 border-transparent hover:border-[#97bc62]"
            >
              <div class="flex items-center space-x-3">
                <div class="h-8 w-8 bg-[#2c5f2d] rounded-full flex items-center justify-center">
                  <span class="text-white font-bold text-sm">{{ language[0] }}</span>
                </div>
                <span class="text-gray-800 font-medium group-hover:text-[#2c5f2d] transition-colors">
                  {{ language }}
                </span>
              </div>
            </li>
          </ul>
        </section>
      </div>
    </main>

    <!-- Footer -->
    <footer class="bg-[#2c5f2d] text-white">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <!-- Columna Fundación -->
          <div class="flex flex-col items-center md:items-start space-y-4">
            <img :src="openwiki_logo" class="w-16 h-16" alt="Logo de OpenWiki" />
            <p class="text-sm text-center md:text-left text-gray-100">
              OpenWiki es un proyecto de la Fundación OpenWiki, organización sin fines de lucro comprometida con la preservación del patrimonio cultural lingüístico.
              Creador por <a href="https://github.com/juan-pd/" target="_blank" class="underline cursor-pointer">Juan de Dios</a>.
            </p>
          </div>

          <!-- Proyectos relacionados -->
          <div class="space-y-4">
            <h3 class="text-lg font-bold mb-4 text-center md:text-left">Nuestros Proyectos</h3>
            <div class="space-y-3">
              <a
                href="#"
                class="flex items-center space-x-3 px-4 py-3 rounded-lg hover:bg-[#97bc62]/20 transition-colors"
              >
                <div class="h-6 w-6 bg-white rounded-full flex items-center justify-center">
                  <span class="text-[#2c5f2d] font-bold text-sm">C</span>
                </div>
                <div>
                  <p class="font-medium">Culturapedia</p>
                  <p class="text-sm text-gray-200">Enciclopedia cultural colaborativa</p>
                </div>
              </a>
              <a
                href="#"
                class="flex items-center space-x-3 px-4 py-3 rounded-lg hover:bg-[#97bc62]/20 transition-colors"
              >
                <div class="h-6 w-6 bg-white rounded-full flex items-center justify-center">
                  <span class="text-[#2c5f2d] font-bold text-sm">D</span>
                </div>
                <div>
                  <p class="font-medium">OpenDiccionario</p>
                  <p class="text-sm text-gray-200">Diccionario multilingüe indígena</p>
                </div>
              </a>
            </div>
          </div>

          <!-- Información legal -->
          <div class="text-center md:text-right space-y-2">
            <p class="text-sm text-gray-200">
              Licencia Creative Commons CC-BY-SA 4.0
            </p>
            <p class="text-sm text-gray-200">
              Políticas de privacidad
            </p>
            <p class="text-sm text-gray-200">
              Código de conducta
            </p>
          </div>
        </div>

        <!-- Derechos de autor -->
        <div class="border-t border-[#97bc62]/30 mt-8 pt-8 text-center">
          <p class="text-sm text-gray-200">
            © 2024 OpenWiki. Todos los derechos compartidos.
            <span class="block sm:inline">Construido con el corazón por comunidades indígenas.</span>
          </p>
        </div>
      </div>
    </footer>
  </div>
</template>
