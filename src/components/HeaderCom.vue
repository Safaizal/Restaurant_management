<template>

    <div class="nav">
        <a href="#">Home</a>
        <a href="#">Add Restaurant</a>
        <a href="#">Update Restaurant</a>
        <a href="#">Logout</a>
    </div>

</template>

<script>

export default {
    name : "HeaderCom"
}

</script>

<style>
.nav{
    background-color: black;
    overflow: hidden;
}
.nav a{
    float: left;
    color: white;
    padding: 15px 15px;
    text-align: center;
    text-decoration: none;
    margin-right: 10px;
}
.nav a:hover{
    background-color: white;
    color: black;
    transition: 500ms;
}
</style>
