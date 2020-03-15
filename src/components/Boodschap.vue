<template>
    <div class="boodschap" v-bind:class="{'is-complete':boodschap.completed}">
        <p>
            <input type="checkbox" @change="markComplete">
            {{boodschap.title}}
            <input class="aantalVeld" id = "aantal" min="1" type="number" />
            <button class="navigatiebutton" @click="$emit('boodschap-omhoog', index)"> ↑ </button>
            <button class="navigatiebutton"  @click="$emit('boodschap-omlaag', index)"> ↓ </button>
            <button @click="$emit('del-boodschap', boodschap.id)" class="del"> X </button>
        </p>
    </div>
</template>

<script>
    export default {
        name: "Boodschap",
        props: ["boodschap", "index", "arraySize"],
        methods: {
            markComplete() {
                this.boodschap.completed = !this.boodschap.completed;
                this.$emit('boodschap-aangevinkt')

            }
        }
    }
</script>

<style scoped>
    .boodschap {
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .aantalVeld {
        margin-left: 20px;
    }

    .is-complete {
        text-decoration: line-through;
        background: grey;
    }

    .del {
        background: darkred;
        color: #fff;
        border: gray;
        padding: 5px 15px;
        cursor: pointer;
        float: right;
    }

    @media only screen and (max-width: 600px) {
        .boodschap{

        }

                .navigatiebutton {
            display: none;
        }
    }

</style>