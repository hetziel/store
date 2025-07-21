<template>
  <div class="catalogo-container">
    <h1 class="catalogo-title">Catálogo de Productos</h1>
    <div class="productos-grid">
      <div v-for="producto in productos" :key="producto.id" class="producto-card">
        <img :src="producto.imagen + '-300x300.png'" alt="Imagen del producto" class="producto-imagen" />
        <h2 class="producto-nombre">{{ producto.nombre }}</h2>
        <p class="producto-descripcion">{{ producto.descripcion }}</p>
        <a
          class="producto-btn"
          :href="whatsappLink(producto.nombre)"
          target="_blank"
          rel="noopener"
        >
          Consultar precio
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const productos = ref([])

onMounted(async () => {
  const res = await fetch('/src/data/productos.json')
  productos.value = await res.json()
})

// Reemplaza el número por el tuyo en formato internacional, ej: 5215551234567
const whatsappNumber = '584148605048'

function whatsappLink(nombre) {
  const mensaje = encodeURIComponent(`Hola, quiero consultar el precio del vehículo: ${nombre}`)
  return `https://wa.me/${whatsappNumber}?text=${mensaje}`
}
</script>

<style scoped>
.catalogo-container {
  max-width: 1200px;
  padding: 24px;
  background: #f8fafc;
  border-radius: 16px;
  box-shadow: 0 8px 32px rgba(60, 60, 120, 0.08);
}

.catalogo-title {
  text-align: center;
  font-size: 2.5rem;
  color: #ba0707;
  margin-bottom: 32px;
  font-weight: 700;
  letter-spacing: 2px;
}

.productos-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 32px;
}

.producto-card {
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 4px 16px rgba(60, 60, 120, 0.07);
  padding: 24px;
  display: flex;
  flex-direction: column;
  align-items: center;
  transition: transform 0.2s, box-shadow 0.2s;
}

.producto-card:hover {
  transform: translateY(-6px) scale(1.03);
  box-shadow: 0 8px 32px rgba(60, 60, 120, 0.13);
}

.producto-imagen {
  width: 120px;
  height: 120px;
  object-fit: cover;
  border-radius: 8px;
  margin-bottom: 16px;
  box-shadow: 0 2px 8px rgba(60, 60, 120, 0.09);
}

.producto-nombre {
  font-size: 1.3rem;
  color: #1e293b;
  font-weight: 600;
  margin-bottom: 8px;
  text-align: center;
}

.producto-descripcion {
  font-size: 1rem;
  color: #64748b;
  margin-bottom: 12px;
  text-align: center;
}

.producto-precio {
  font-size: 1.2rem;
  color: #10b981;
  font-weight: 700;
  margin-bottom: 16px;
}

.producto-btn {
  background: linear-gradient(90deg, #3b82f6 0%, #6366f1 100%);
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 10px 24px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
  box-shadow: 0 2px 8px rgba(60, 60, 120, 0.09);
}

.producto-btn:hover {
  background: linear-gradient(90deg, #6366f1 0%, #3b82f6 100%);
}
</style>