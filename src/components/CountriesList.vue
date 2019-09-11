<template lang="html">
    <div>
        <ul>
            <list-item v-for="(country, index) in countries" v-bind:country="country" v-bind:key="index">{{countries.name}}</list-item>
        </ul>
    </div>
</template>

<script>
    import ListItem from './ListItem.vue';

    export default {
        name: 'countries-list',
        props: ['countries'],
        components: {
            "list-item": ListItem
        }

    }
</script>

<style lan="css" scoped>

</style>