<script setup>
import openwiki_logo from '@/assets/img/openwiki.png'
</script>

<template>
  <nav
    class="flex justify-between items-center max-w-7xl mx-auto px-4 py-2"
  >
    <div class="flex items-center gap-x-10">
      <img :src="openwiki_logo" class="w-20" alt="Logo de OpenWiki" />
      <div class="flex">
        <input
          type="text"
          placeholder="Buscar en openwiki"
          class="p-1 w-84 border border-gray-300 focus:ring-2 focus:ring-blue-500"
          aria-label="Buscar en el sitio"
        />
        <button
          class="p-1 px-4 bg-blue-500 text-white hover:bg-blue-600 focus:outline-none focus:ring-2 focus:ring-blue-500"
        >
          Buscar
        </button>
      </div>
    </div>
    <div class="flex gap-x-6">
      <router-link to="/login" class="p-2 text-gray-700 hover:text-blue-500 transition duration-300"
        >Iniciar sesión</router-link
      >
      <router-link
        to="/register"
        class="p-2 text-gray-700 hover:text-blue-500 transition duration-300"
        >Registrarse</router-link
      >
    </div>
  </nav>
</template>
