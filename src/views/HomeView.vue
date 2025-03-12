<script setup>
import HeaderNavbar from '@/components/HeaderNavbar.vue'
import FooterNavbar from '@/components/FooterNavbar.vue'

const languages = [
  'Náhuatl',
  'Maya',
  'Mixteco',
  'Zapoteco',
  'Otomi',
  'Tzeltal',
  'Tzotzil',
  'Mazahua',
  'Chol',
  'Purépecha',
  'Huasteco',
  'Totonaca',
  'Rarámuri',
  'Yaqui',
  'Triqui',
  'Amuzgo',
  'Chichimeca',
  'Tojolabal',
  'Cholulteco',
  'Huichol',
  'Pipil',
  'Ixcateco',
  'Kumiai',
  'Seri',
  'Pame',
  'Cora',
  'Mixe',
  'Zoque',
  'Ayapaneco',
  'Popoloca',
  'Mazateco',
  'Cuicateco',
]
</script>

<template>
  <div class="min-h-screen flex flex-col">
    <!-- Header -->
    <HeaderNavbar />

    <!-- Main content -->
    <main>
      <!-- Languages Section -->
      <section class="py-16 bg-gray-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div class="text-center mb-12">
            <h2 class="text-3xl font-bold text-gray-900 sm:text-4xl">
              Lenguas Indígenas de México
            </h2>
            <p class="mt-4 text-lg text-gray-600 max-w-3xl mx-auto">
              México es hogar de una rica diversidad lingüística con más de 68 lenguas indígenas y 
              364 variantes. Aquí presentamos algunas de ellas, pero sabemos que hay muchas más.
            </p>
          </div>

          <!-- Language Tags -->
          <div class="flex flex-wrap justify-center gap-3 mb-12">
            <div 
              v-for="language in languages" 
              :key="language"
              class="px-4 py-2 bg-white rounded-full shadow-sm border border-gray-200 text-[#2c5f2d] hover:bg-[#2c5f2d] hover:text-white transition-colors duration-200 cursor-pointer"
            >
              {{ language }}
            </div>
          </div>

          <!-- Call to Action -->
          <div class="bg-gradient-to-r from-[#2c5f2d] to-[#1e3f1f] rounded-xl shadow-xl overflow-hidden">
            <div class="px-6 py-12 md:p-12 text-center md:text-left md:flex md:items-center md:justify-between">
              <div class="md:flex-1">
                <h3 class="text-2xl font-bold text-white">
                  ¿Conoces una lengua que no está en nuestra lista?
                </h3>
                <p class="mt-2 text-gray-100 md:pr-12">
                  Si conoces una lengua indígena o una variante que no aparece aquí, te invitamos a 
                  registrarte y contribuir con tu conocimiento. Cada aporte es valioso para preservar 
                  nuestro patrimonio lingüístico.
                </p>
              </div>
              <div class="mt-8 md:mt-0 flex flex-col sm:flex-row justify-center md:justify-start gap-4">
                <router-link
                  to="/register"
                  class="inline-flex items-center justify-center px-6 py-3 border border-transparent text-base font-medium rounded-md text-[#2c5f2d] bg-white hover:bg-gray-100 transition duration-300"
                >
                  Registrarse
                </router-link>
                <router-link
                  to="/contribute"
                  class="inline-flex items-center justify-center px-6 py-3 border border-[#97bc62] text-base font-medium rounded-md text-white hover:bg-[#97bc62]/30 transition duration-300"
                >
                  Contribuir
                </router-link>
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>

    <!-- Footer -->
    <FooterNavbar />
  </div>
</template>
