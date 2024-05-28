<script setup lang="ts">
useHead({
  titleTemplate: (titleChunk) => {
    return titleChunk ? `${titleChunk} · EM Cosmetics` : 'EM Cosmetics'
  },
  link: [{ rel: 'icon', type: "image/x-icon", href: '/icons/favicon.ico' }]
})
</script>

<template>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com">
  <link href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap" rel="stylesheet">
  <div>
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </div>
</template>

<style>
/* width */
::-webkit-scrollbar {
  width: 8px;
}

/* Track */
::-webkit-scrollbar-track {
  background: inherit; 
}
 
/* Handle */
::-webkit-scrollbar-thumb {
  background: rgb(139, 139, 139); 
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #403D3D; 
}
</style>