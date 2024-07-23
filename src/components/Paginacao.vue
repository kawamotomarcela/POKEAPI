<script setup>
import { defineProps, computed } from 'vue';

const props = defineProps({
  currentPage: Number,
  totalPages: Number,
  changePage: Function,
});

const visiblePages = computed(() => {
    const pages = [];
    const totalVisible = 3;
    let startPage = Math.max(props.currentPage - 1, 1);
    let endPage = Math.min(startPage + totalVisible - 1, props.totalPages);

    if (endPage - startPage < totalVisible - 1) {
        startPage = Math.max(endPage - totalVisible + 1, 1);
    }

    for (let i = startPage; i <= endPage; i++) {
        pages.push(i);
    }
    return pages;
});
</script>

<template>
    <nav aria-label="Page navigation example" class="mt-3">
        <ul class="pagination justify-content-end mt-4">
            <li class="page-item" :class="{ disabled: props.currentPage === 1 }">
                <a class="page-link" href="#" @click.prevent="props.changePage(props.currentPage - 1)">Anterior</a>
            </li>
            <li class="page-item" v-for="page in visiblePages" :key="page" :class="{ active: props.currentPage === page }">
                <a class="page-link" href="#" @click.prevent="props.changePage(page)">{{ page }}</a>
            </li>
            <li class="page-item" :class="{ disabled: props.currentPage === props.totalPages }">
                <a class="page-link" href="#" @click.prevent="props.changePage(props.currentPage + 1)">Próximo</a>
            </li>
        </ul>
    </nav>
</template>
