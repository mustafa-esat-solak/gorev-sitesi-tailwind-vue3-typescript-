<template>
  <div class="maksimum-genislik mx-auto mt-10 p-6 bg-white shadow yuvarlak">
    <h1 class="text-xl font-bold mb-4 text-merkez">Görev Listesi</h1>

    <div class="flex bosluk-arasi mb-4">
      <input
        v-model="yeniGorev"
        type="text"
        placeholder="Yeni görev girin..."
        class="border p-2 esnek yuvarlak"
      />
      <button @click="gorevEkle" class="bg-mavi text-white p-2 yuvarlak">
        Ekle
      </button>
    </div>

    <ul class="liste list-disc ml-5">
      <li
        v-for="(gorev, index) in gorevler"
        :key="index"
        class="flex justify-between items-center mb-2"
      >
        <span>{{ gorev }}</span>
        <button
          @click="gorevSil(index)"
          class="text-kirmizi hover:underline text-sm"
        >
          Sil
        </button>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'

export default defineComponent({
  setup() {
    const yeniGorev = ref('')
    const gorevler = ref<string[]>([])

    const gorevEkle = () => {
      if (yeniGorev.value.trim()) {
        gorevler.value.push(yeniGorev.value.trim())
        yeniGorev.value = ''
      }
    }

    const gorevSil = (index: number) => {
      gorevler.value.splice(index, 1)
    }

    return {
      yeniGorev,
      gorevler,
      gorevEkle,
      gorevSil,
    }
  },
})
</script>

<style scoped>
.maksimum-genislik {
  max-width: 500px;
}
.yuvarlak {
  border-radius: 0.5rem;
}
.text-merkez {
  text-align: center;
}
.bosluk-arasi > * + * {
  margin-left: 0.5rem;
}
.esnek {
  flex: 1;
}
.bg-mavi {
  background-color: #3b82f6;
}
.text-kirmizi {
  color: #ef4444;
}
</style>