<template>
    <div class="card">
        <div class="card-body">
            <slot></slot>
        </div>
    </div>
</template>

<script>
export default {
    name: "CardComp"
}
</script>

<style scoped>
.card {
    width: 18rem;
}
</style>