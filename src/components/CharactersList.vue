<template>
    <h1>Welcome to Star Wars Encyclopedia</h1>
    <div>
        <CharacterCard :character="character" />
    </div>
</template>

<script lang="ts">
    import CharacterCard from './CharacterCard.vue'
    import { defineComponent } from 'vue';
    import type { CharacterModel } from '@/models/character'
    import axios from 'axios'
    
    export default defineComponent ({
        data() {
            return {
                character: {} as CharacterModel,
            };
        },
        async created() {
            const response = await axios.get<CharacterModel>("https://swapi.dev/api/people/1");
            const {data} = await axios.get<CharacterModel[]>("https://swapi.dev/api/people")
            console.log(data)
            this.character = response.data
        },
        components: { CharacterCard }
    })
</script>

<style scoped>

</style>