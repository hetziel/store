<template>
  <section class="hero">
    <div class="hero-overlay"></div>
    <div class="hero-content">
      <h2 class="hero-title">MM4WD TIENE LOS MEJORES VEHICULOS PARA TI</h2>
      <p class="hero-desc">
        Estamos atendiendo en la ciudad de Upata.
        Explora nuestra selección de vehículos y consulta fácilmente por WhatsApp. Encuentra el modelo perfecto para ti.
      </p>
      <a href="#catalogo" class="hero-btn">Ver catálogo</a>
    </div>
  </section>
</template>

<style scoped>
.hero {
  width: 100%;
  min-height: 320px;
  background: linear-gradient(90deg, #ef444494 0%, #0000008c 100%), url('/src/assets/hero.jpg') center/cover no-repeat;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 64px 16px 48px 16px;
  margin-top: 80px;
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
}

.hero-overlay {
  position: absolute;
  inset: 0;
  /* background: linear-gradient(90deg, #ef4444cc 0%, #b91c1ccc 100%); */
  z-index: 1;
}

.hero-content {
  max-width: 700px;
  text-align: center;
  position: relative;
  z-index: 2;
}

.hero-title {
  font-size: 2.5rem;
  font-weight: 800;
  margin-bottom: 18px;
  letter-spacing: 1px;
}

.hero-desc {
  font-size: 1.2rem;
  margin-bottom: 28px;
  color: #ffe4e6;
}

.hero-btn {
  display: inline-block;
  background: #fff;
  color: #b91c1c;
  font-weight: 700;
  font-size: 1.1rem;
  padding: 12px 32px;
  border-radius: 8px;
  text-decoration: none;
  transition: background 0.2s, color 0.2s;
  box-shadow: 0 2px 8px rgba(239, 68, 68, 0.13);
}

.hero-btn:hover {
  background: #b91c1c;
  color: #fff;
}
</style>