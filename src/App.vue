<script setup lang="ts">
import NavBar from '@/components/NavBar.vue'
</script>

<template>
  <div class="layout">
    <NavBar />
    <main class="content">
      <RouterView />
    </main>
  </div>
</template>

<style scoped>
.layout {
  min-height: 100vh;
  width: 100vw;
  background: linear-gradient(135deg, #fafdff 0%, #e3eafc 100%);
  box-sizing: border-box;
  overflow-x: hidden;
}

.content {
  padding: 0;
  background: transparent;
  min-height: calc(100vh - 64px);
  width: 100vw;
  box-sizing: border-box;
}

/* 移动端适配 */
@media (max-width: 768px) {
  .content {
    min-height: calc(100vh - 56px);
  }
}

@media (max-width: 480px) {
  .content {
    min-height: calc(100vh - 52px);
  }
}
</style>
