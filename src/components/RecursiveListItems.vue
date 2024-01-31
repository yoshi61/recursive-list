<template>
  <div v-for="item in items" :key="item.id">
    <template v-if="hasChildren(item)">
        <div>
            <div class="spacer" :style="`width: ${level*1}rem`" />
            <div class="toggle-icon bullet" @click="toggle = !toggle">{{ toggle? "▶" : "▼" }} </div>
            {{ item.name }}
        </div>
        <div v-show="!toggle">
            <recursive-list-items :items="item.children" :level="level+1" />
        </div>
    </template>
    <template v-else>
      <div>
          <div class="spacer" :style="`width: ${level*1}rem`" /><div class="bullet">•</div>
          {{ item.name }}
      </div>
    </template>
  </div>
</template>

<script>
export default {
    name: "RecursiveListItems",
    data() {
        return {
            toggle: false
        };
    },

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

<style scoped>
.bullet {
    display: inline-block;
    text-align: center;
    width: 1rem;
}
.spacer {
    display: inline-block;
}
.toggle-icon {
    cursor: pointer;
}
</style>
