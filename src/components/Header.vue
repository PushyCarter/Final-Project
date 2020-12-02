<template>
    <div class="header">
        <h1>{{title}}</h1>
    </div>
</template>

<script>
export default {
    name: "Header",
    props: ['title']
}
</script>

<style scoped>
    .header
        {
            background: #333;
            color: white;
            text-align: center;
            padding: 10px;
            margin: 0px;
        }
</style>