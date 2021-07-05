<template>
  <a v-if="isExternalLink" 
    target="_blank"
    class="normal-link"
    :href="link.to">{{ link.name }}</a>

    <router-link
        v-else
        :to="{ name: link.to, params: { id: link.id } }"
        v-slot="{ isActive }"
    >
        <!-- href, isActive -->
        <a :class="isActive ? 'is-active' : 'normal-link'">
            {{ link.name }}
        </a>
    </router-link>
</template>

<script>
export default {
    props: {
        link: {
            type: Object,
            required: true
        }
    },
    computed: {
        isExternalLink() {
            return this.link.to.startsWith('http')
        }
    }
}
</script>

<style scoped>
.is-active {
    color: #42b983;
}
.normal-link {
    color: #c6c5c5;
}
</style>