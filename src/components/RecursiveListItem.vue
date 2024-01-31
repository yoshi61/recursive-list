<template>
    <template v-if="hasChildren(item)">
        <div>
            <div class="spacer" :style="`width: ${level*1}rem`" />
            <div class="toggle-icon bullet" @click="expand = !expand">{{ expand? "▼" : "▶" }} </div>
            {{ item.name }}
        </div>
        <div v-show="expand">
            <recursive-list-item v-for="child in item.children" :item="child" :level="level+1" :parentExpand="expand" :key="child.id" />
        </div>
    </template>
    <template v-else>
        <div>
            <div class="spacer" :style="`width: ${level*1}rem`" /><div class="bullet">•</div>
            {{ item.name }}
        </div>
    </template>
</template>

<script>
export default {
    name: "RecursiveListItem",
    data() {
        return {
            expand: true
        }
    },

    props: {
        item: {
            required: true,
            type: Object
        },
        level: {
            type:Number,
            default: 0
        },
        parentExpand: {
            type: Boolean,
            default: false
        }
    },
    watch: {
        parentExpand(v) {
            if(!v) {
                this.expand = false;
            }
        }
    },
    methods: {
        hasChildren(item) {
            return item?.children && item?.children.length > 0;
        }
    },
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
