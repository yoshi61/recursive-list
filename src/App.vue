<template>
    <div v-for="item in listData" :key="item.id">
        {{item}}
    </div>
</template>

<script>
import { fetchData } from "./fetchData.js";
export default {
    name: "App",
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
