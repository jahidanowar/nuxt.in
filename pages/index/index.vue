<script lang="ts" setup>
const { data } = await useAsyncData("subdomain", (ctx) => {
  const host: string = ctx.ssrContext.event.req.headers.host;
  const subdomain: string = host.split(".")[0];
  return Promise.resolve(subdomain);
});

useHead({
  title: data ? `${data.value}'s Learning centre` : "Master Nuxt.js in Hindi",
});
</script>
<template>
  <div class="h-screen grid place-content-center text-center">
    <h1 v-if="!data">coming soon</h1>
    <h1 v-else>
      Hey
      <span
        class="font-boold font-mono bg-blue-100 text-blue-500 py-1 px-2 rounded-lg"
        >{{ data }}</span
      >, You see what we did there? <br />
      You will have your own practice centre.
    </h1>
  </div>
</template>
