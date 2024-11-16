<template>
    <div >
        <ul class="nav nav-tabs">
            <li v-for="tab in tabs" :key="tab" class="nav-item">
                <a href="javascript:void(0)" class="nav-link" :class="{ active: tab === selected }"
                    @click="setTab(tab)">
                    {{ tab }}
                </a>
            </li>
        </ul>
        <slot></slot>
    </div>
</template>

<script>
export default {
    props: {
        tabs: {
            type: Array,
            required: true,
        },
        selected: {
            type: String,
            required: true,
        }
    },
    methods: {
        setTab(tab) {
            this.$emit('selected', tab);
        }
    }
}
</script>

<style scoped>
.nav-tabs {
    display: flex;
}

.nav-item {
    margin-right: 10px;
}

.nav-link {
    padding: 10px;
    text-decoration: none;
    border: 1px solid transparent;
    cursor: pointer;
    color: #007bff;
}

.nav-link.active{
    border-bottom: 1px solid white;
}

ul{
    list-style: none;
    margin-bottom: 10px;
}
</style>