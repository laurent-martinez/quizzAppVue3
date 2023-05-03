<script setup>
    const props = defineProps(['questionStatus'])
</script>


<template>
    <div>
        <header>
            <h3>Question {{props.questionStatus}}</h3>
            <div class="bar">
                <div class="completion"></div>
            </div>
        </header>
    </div>
</template>

<style scoped>
header {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100px;
    background-color: #C9C6E4;
}
header h3 {
    margin: 0;
    font-size: 1.5rem;
    font-weight: 400;
}
.bar {
    width: 300px;
    height: 10px;
    background-color: #e0e0e0;
    border-radius: 5px;
    margin-top: 10px;
}
.frog {
    width: 50px;
    height: 50px;
    margin-top: 10px;
}
.completion {
    width: 0%;
    height: 100%;
    background-color: #4caf50;
    border-radius: 5px;
}
</style>