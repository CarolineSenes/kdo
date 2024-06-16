<script setup>
import { createClient } from "@supabase/supabase-js";

const supabase = createClient(
  "https://qkfsxmmtbbjlssurdkxf.supabase.co",
  "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InFrZnN4bW10YmJqbHNzdXJka3hmIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MTc4NzE2NjIsImV4cCI6MjAzMzQ0NzY2Mn0.plZ6w_UNWFJwibjEQXRSKraq9Ll3xqFgGhFgV8fMZt4"
);
const gifts = ref([]);

async function getGifts() {
  const { data, error } = await supabase.from("gifts").select("*");
  if (error)
    console.error("Erreur lors de la récupération des cadeaux:", error);
  else gifts.value = data;
}

onMounted(() => {
  getGifts();
});
</script>

<template>
  <div>
    <NuxtRouteAnnouncer />
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </div>
</template>
