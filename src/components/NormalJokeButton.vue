<template>
    <div>
        
        <div v-if="joke !== undefined">
             <h4>{{ joke }}</h4>
        </div>
       
    </div>
</template>

<script>
    export default {
        data() {
            return {
                joke: undefined
            }
        },

        methods: {
            display_joke(normal_joke) {
                this.joke = normal_joke
            }
        },

        mounted () {
            this.$root.$on(`random_joke`, this.display_joke);
        },
    }
</script>

<style scoped>

</style>