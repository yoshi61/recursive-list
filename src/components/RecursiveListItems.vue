<template>
  <div v-for="item in items" :key="item.id">
    <template v-if="hasChildren(item)">
        <div>
            {{ item.name }}
        </div>
        <div>
            <recursive-list-items :items="item.children" :level="level+1" />
        </div>
    </template>
    <template v-else>
      <div>
          {{ item.name }}
      </div>
    </template>
  </div>
</template>

<script>
export default {
    name: "RecursiveListItems",

    props: {
        items: {
            required: true,
            type: Array
        },
        level: {
            type:Number,
            default: 0
        }
    },
    methods: {
        hasChildren(item) {
            return item?.children && item?.children.length > 0;
        }
    }
}
</script>

<style>
</style>
