<template>
  <div class="catalogo-container">
    <h1 class="catalogo-title">Catálogo de Productos</h1>
    <div class="productos-lista">
      <div v-for="producto in productos" :key="producto.id" class="producto-item">
        <div class="producto-imagen-container">
          <img :src="producto.imagen + '-300x300.png'" alt="Imagen del producto" class="producto-imagen" />
        </div>
        <div class="producto-contenido">
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
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const productos = ref([])

onMounted(async () => {
  const res = await fetch('./data/productos.json')
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
  padding: 16px;
  background: #f8fafc;
  border-radius: 16px;
  box-shadow: 0 8px 32px rgba(60, 60, 120, 0.08);
}

.catalogo-title {
  text-align: center;
  font-size: 1.8rem;
  color: #ba0707;
  margin-bottom: 24px;
  font-weight: 700;
  letter-spacing: 1px;
}

.productos-lista {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.producto-item {
  display: flex;
  align-items: flex-start;
  gap: 16px;
  background: #fff;
  border-radius: 12px;
  padding: 16px;
  box-shadow: 0 2px 8px rgba(60, 60, 120, 0.07);
  transition: transform 0.2s, box-shadow 0.2s;
}

.producto-item:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 16px rgba(60, 60, 120, 0.12);
}

.producto-imagen-container {
  flex: 0 0 80px;
  height: 80px;
  border-radius: 8px;
  overflow: hidden;
}

.producto-imagen {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.producto-contenido {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.producto-nombre {
  font-size: 1.1rem;
  color: #1e293b;
  font-weight: 600;
  margin: 0;
}

.producto-descripcion {
  font-size: 0.9rem;
  color: #64748b;
  margin: 0;
}

.producto-btn {
  background: linear-gradient(90deg, #3b82f6 0%, #6366f1 100%);
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 8px 16px;
  font-size: 0.9rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
  box-shadow: 0 1px 4px rgba(60, 60, 120, 0.09);
  text-decoration: none;
  text-align: center;
  align-self: flex-start;
  margin-top: 8px;
}

.producto-btn:hover {
  background: linear-gradient(90deg, #6366f1 0%, #3b82f6 100%);
}

/* Estilos específicos para móvil */
@media (max-width: 768px) {
  .catalogo-container {
    padding: 12px;
  }
  
  .catalogo-title {
    font-size: 1.5rem;
    margin-bottom: 16px;
  }
  
  .producto-item {
    padding: 12px;
    gap: 12px;
  }
  
  .producto-imagen-container {
    flex: 0 0 60px;
    height: 60px;
  }
  
  .producto-nombre {
    font-size: 1rem;
  }
  
  .producto-descripcion {
    font-size: 0.85rem;
  }
  
  .producto-btn {
    padding: 6px 12px;
    font-size: 0.85rem;
  }
}
</style>