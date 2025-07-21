<template>
  <header class="header">
    <img src="/src/assets/Logo-MM4WD.png" alt="Logo" class="logo" />
    <h1 class="titulo">Catálogo de Productos</h1>
  </header>
</template>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  z-index: 100;
  display: flex;
  align-items: center;
  gap: 18px;
  padding: 18px 32px;
  background: black;
  color: #fff;
  box-shadow: 0 2px 12px rgba(239, 68, 68, 0.13);
}

.logo {
  width: 48px;
  height: 48px;
  object-fit: contain;
}

.titulo {
  font-size: 2rem;
  font-weight: 700;
  letter-spacing: 2px;
}
</style>