<template>
    <nav class="light-blue darken-3">
        <div class="nav-wrapper ">
            <router-link to="/" class="brand-logo">Задания</router-link>
            <ul class="right hide-on-med-and-down flex-column">
                <li><router-link tag="li" to="/" exact active-class="active"><a href="#">Создать</a></router-link></li>
                <li><router-link tag="li" to="/list"   active-class="active"><a href="#" class="light-blue darken-3">Список</a></router-link></li>
            </ul>
        </div>
    </nav>
</template>

<script>
</script>

<style lang="scss" scoped>
    nav {
        padding: 0 2rem;
    }

</style>