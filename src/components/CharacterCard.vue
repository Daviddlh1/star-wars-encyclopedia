<template>     
    <div class="card">
        <h1>Esta es una card</h1>
        <p>Name: {{ character?.name }}</p>
        <p>Height: {{ character?.height }}</p>
        <p>Mass: {{ character?.mass }}</p>
        <p>Gender: {{ character?.gender }}</p>
        <p>Home world: {{ character?.homeworld }}</p>
        
    </div>
</template>

<script lang="ts">
import type { CharacterModel } from '@/models/character'
import type { PropType } from 'vue';
    export default{
        props: {
            character: {} as PropType<CharacterModel>,
        },
        data() {
            return {
                characterId: "" as string | undefined
            }
        },
        updated() {
            this.characterId = this.character?.url?.charAt(this.character.url.length - 2)
            console.log('characterID', this.characterId)
        },
    }
</script>

<style scoped>
.card {
    width: 250px;
    height: 350px;
    border: 1px solid red;
}
</style>