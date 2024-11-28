<template>
<div v-if="coches.length" id="carouselExampleIndicators" class="carousel slide" data-bs-ride="carousel">
    <div class="carousel-inner">
    <div 
        v-for="(coche, index) in coches" 
        :key="coche.id" 
        :class="['carousel-item',{ active: index === 0 }]"
    >
        <img :src="`${rutaBase}/${coche.imagen}`" class="d-block w-100" :alt="`${coche.marca} ${coche.modelo}`" />
        <div class="carousel-caption d-none d-md-block">
        <h5>{{ coche.marca }} - {{ coche.modelo }}</h5>
        <p>Precio: ${{ coche.precio.toLocaleString() }}</p>
        </div>
    </div>
    </div>
    <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Previous</span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Next</span>
    </button>
</div>
<div v-else class="text-center">Cargando datos...</div>
</template>

<script>
import axios from 'axios';


export default {
name: "Carousel",
data() {
    return {
    coches: [],
    rutaBase: 'http://localhost:8000'
    };
},
methods: {
    async fetchCoches() {
    try {
        const response = await axios.get("http://localhost:8000/allcoches");
        this.coches = response.data;
    } catch (error) {
        console.error("Error al cargar los coches:", error);
    }
    },
},
mounted(){
    this.fetchCoches();
}
};
</script>

<style scoped>
.carousel-item img {
height: 400px;
object-fit: cover;
}

.carousel-caption {
background: rgba(0, 0, 0, 0.5);
padding: 15px;
border-radius: 10px;
}
</style>
