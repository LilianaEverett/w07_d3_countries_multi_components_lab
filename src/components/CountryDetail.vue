<template>
    <article v-if="country">
        <p>{{ country.name }}</p>
        <p>{{ country.capital }}</p>
        <p>{{ country.population }}</p>
        <p>{{ country.flag }}</p>
    </article>
</template>

<script>
    export default {
        name: 'country-detail',
        props: ['country']
    }
</script>

<style>

</style>