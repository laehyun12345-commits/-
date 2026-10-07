<script setup>
const props = defineProps({
    title: String,
    status: String
});
</script>

<template>
    <article class="issue-item">
        <h4>{{props.title}}</h4>
        <span class="status">{{props.status}}</span>
        <button>삭제</button>
    </article>
</template>

<style scoped>
.issue-item {
        h4 {
            font-size: 16px;
            margin: 0;
        }

        .status {
            display: inline-block;
            background-color: green;
            color: white;
            height: 32px;
            line-height: 32px;
            text-align: center;
            width: 100px;
            border-radius: 16px;
        }
    }
</style>