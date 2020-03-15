<template>
    <header class="header">
        <h1>BoodschApp</h1>
    </header>
</template>

<script>
    export default {
        name: "Header"
    }
</script>

<style scoped>
    .header{
        background: darkcyan;
        color: white;
        text-align: center;
        padding: 10px;
        font-size: 40px;
    }

    @media only screen and (max-width: 768px){
        .header{
            font-size: 20px;
        }
    }


</style>