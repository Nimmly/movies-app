<template>
    <div>
        <b-input
        class='mb-2 mr-sm-2 mb-sm-0'
        @input="emitInputChangeEvent"
        />
    </div>
</template>

<script>
export default {
    methods:{
        emitInputChangeEvent(term){
            this.$emit('search-term-change', term)
        }
    }
}
</script>

<style>

</style>
