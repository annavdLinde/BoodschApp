<template>
    <div>
        <div v-bind:key="boodschap.id" v-for="(boodschap, index) in boodschappen">
            <Boodschap v-bind:boodschap="boodschap"
                       v-bind:index="index"
                       v-bind:arraySize="arraySize=boodschappen.length"
                       v-on:del-boodschap="$emit('del-boodschap', boodschap.id)"
                       v-on:boodschap-aangevinkt="$emit('boodschap-aangevinkt')"
                       v-on:boodschap-omhoog="$emit('boodschap-omhoog', index)"
                       v-on:boodschap-omlaag="$emit('boodschap-omlaag', index)"
            />
        </div>
    </div>
</template>

<script>
import Boodschap from "./Boodschap";

export default{
    name: "Boodschappen",
    props: ["boodschappen"],
    components: {
        Boodschap
    }

}
</script>


<style scoped>

</style>