<template>
    <div class="alert alert-danger text-center">
        <h1>Sorry, wrong answer!</h1>
        <hr>
        <button class="btn btn-primary" @click="onTryAgain">Try a New One</button>
    </div>
</template>
<style>

</style>
<script>

    export default{
        methods: {
            onTryAgain() {
                this.$emit('confirmed');
            }
        }
    }
</script>
