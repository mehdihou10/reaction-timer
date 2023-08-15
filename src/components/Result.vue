<template>
    
    <div class="result mt-3">
        <p class="text-secondary fs-5">Reaction Time - {{time}}ms</p>

        <span class="d-block fw-bold fs-3">...{{notice}}</span>
    </div>
</template>

<script>
export default {
    props: ["time","notice"],

}
</script>