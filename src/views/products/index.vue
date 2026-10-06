<script setup lang="ts">
import { ref, onMounted } from "vue";
import Api from "../../api";

// Interface Product
interface Product {
    id: number;
    name: string;
    description: string;
    price: number;
    stock: number;
}

// State products
const products = ref<Product[]>([]);

// Fetch data products dari API
const fetchDataProducts = async () => {
    try {
        const response = await Api.get("/api/product");

        console.log("DATA DARI API:", response.data);

        products.value = response.data;

    } catch (error) {
        console.error("Error fetching products:", error);
    }
};

// Jalankan saat halaman dibuka
onMounted(() => {
    fetchDataProducts();
});

const deleteProduct = async (id: number) => {
    try {

        // delete product berdasarkan id
        await Api.delete(`/api/product/${id}`);

        // refresh data products
        fetchDataProducts();

    } catch (error: any) {

        console.error(
            "Error deleting product:",
            error.response?.data || error
        );
    }
};
</script>

<template>
    <div class="container mt-5 mb-5">
        <div class="row">
            <div class="col-md-12">

                <router-link to="/products/create" class="btn btn-md btn-success rounded-5 shadow border-0 mb-3">
                    ADD NEW PRODUCT
                </router-link>

                <div class="card border-0 rounded-3 shadow">
                    <div class="card-body">

                        <table class="table table-bordered">

                            <thead class="bg-dark text-white">
                                <tr>
                                    <th scope="col">ID</th>
                                    <th scope="col">Name</th>
                                    <th scope="col">Description</th>
                                    <th scope="col">Price</th>
                                    <th scope="col">Stock</th>
                                    <th scope="col" style="width: 15%">
                                        Actions
                                    </th>
                                </tr>
                            </thead>

                            <tbody>

                                <tr v-if="products.length === 0">
                                    <td colspan="6" class="text-center">
                                        <div class="alert alert-danger mb-0">
                                            No data available
                                        </div>
                                    </td>
                                </tr>

                                <tr v-for="product in products" :key="product.id">
                                    <td>{{ product.id }}</td>
                                    <td>{{ product.name }}</td>
                                    <td>{{ product.description }}</td>
                                    <td>{{ Number(product.price).toLocaleString("id-ID", { maximumFractionDigits: 0 }) }}</td>
                                    <td>{{ product.stock }}</td>

                                    <td class="text-center">

                                        <router-link :to="`/products/edit/${product.id}`"
                                            class="btn btn-sm btn-primary rounded-5 shadow border-0 me-2">
                                            EDIT
                                        </router-link>

                                        <button @click="deleteProduct(product.id)"
                                            class="btn btn-sm btn-danger rounded-5 shadow border-0">
                                            DELETE
                                        </button>

                                    </td>
                                </tr>

                            </tbody>

                        </table>

                    </div>
                </div>

            </div>
        </div>
    </div>
</template>

<style scoped>
/* Card tabel */
.card {
    border: 1px solid #e8ebef !important;
    border-radius: 16px !important;
    overflow: hidden;
}

/* Header tabel */
.table thead {
    background-color: #132133 !important;
}

.table thead th {
    color: #ffffff !important;
    background-color: #132133 !important;
    border-color: #26384d !important;
    padding: 15px 16px;
    font-size: 14px;
    font-weight: 600;
    vertical-align: middle;
}

/* Isi tabel */
.table tbody td {
    padding: 14px 16px;
    color: #132133;
    border-color: #edf0f3;
    vertical-align: middle;
}

.table tbody tr {
    transition: background-color 0.2s ease;
}

.table tbody tr:hover {
    background-color: #fffaf0;
}

.btn-success {
    background-color: #ffc107 !important;
    border-color: #ffc107 !important;
    color: #132133 !important;
    font-weight: 600;
}

.btn-success:hover {
    background-color: #e5ad00 !important;
    border-color: #e5ad00 !important;
    color: #132133 !important;
}

.btn-danger {
    background-color: #dc3545 !important;
    border-color: #dc3545 !important;
}

.alert-danger {
    background-color: #fff1f1;
    color: #dc3545;
    border: none;
}
</style>