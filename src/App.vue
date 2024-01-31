<template>
    <recursive-list-item v-for="item in listData" :item="item" :key="item.id" />
</template>

<script>
import { fetchData } from "./fetchData.js";
import RecursiveListItem from "./components/RecursiveListItem";
export default {
    name: "App",
    components: {
        RecursiveListItem
    },
    data() {
        return {
            listData: [],
        };
    },
    async mounted() {
        // init data
        await fetchData().then((data) => {
            this.listData = data;
        });
    },
};
</script>

<style></style>
