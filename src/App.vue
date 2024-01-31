<template>
    <recursive-list-items :items="listData"></recursive-list-items>
</template>

<script>
import { fetchData } from "./fetchData.js";
import RecursiveListItems from "./components/RecursiveListItems";
export default {
    name: "App",
    components: {
        RecursiveListItems
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
