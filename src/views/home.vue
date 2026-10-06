<script setup lang="ts">
</script>

<template>
    <div class="container py-5">
        <div class="row justify-content-center">
            <div class="col-lg-10">
                <div class="hero-card p-4 p-md-5">
                    <div class="hero-content">
                        <span class="badge rounded-pill mb-3">
                            SELAMAT DATANG
                        </span>

                        <h1 class="display-5 fw-bold mb-3">
                            Belajar Membuat Website
                            <span>Modern</span>
                        </h1>

                        <p class="lead text-muted mb-4">
                            Pelajari dasar pembuatan website dengan tampilan
                            yang sederhana, modern, dan mudah dipahami.
                        </p>

                        <button class="btn btn-warning px-4 py-2 fw-semibold">
                            Mulai Belajar
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.container {
    min-height: 100vh;
}

.hero-card {
    position: relative;
    overflow: hidden;
    border-radius: 28px;
    background: linear-gradient(135deg, #132133 0%, #1e344c 100%);
    color: white;
    box-shadow: 0 18px 45px rgba(19, 33, 51, 0.18);
}

.hero-card::before {
    content: "";
    position: absolute;
    width: 230px;
    height: 230px;
    right: -80px;
    top: -80px;
    border-radius: 50%;
    background: rgba(255, 193, 7, 0.14);
}

.hero-card::after {
    content: "";
    position: absolute;
    width: 160px;
    height: 160px;
    left: -70px;
    bottom: -80px;
    border-radius: 50%;
    background: rgba(255, 193, 7, 0.1);
}

.hero-content {
    position: relative;
    z-index: 1;
    max-width: 700px;
}

.badge {
    color: #132133;
    background-color: #ffc107;
    padding: 9px 14px;
    letter-spacing: 1px;
}

.hero-card h1 span {
    color: #ffc107;
}

.hero-card .lead {
    max-width: 600px;
    font-size: 1rem;
    line-height: 1.8;
}

.btn-warning {
    background-color: #ffc107;
    border-color: #ffc107;
    color: #132133;
}

.btn-warning:hover {
    background-color: #e5aa00;
    border-color: #e5aa00;
    color: #132133;
}
</style>