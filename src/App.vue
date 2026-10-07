<script setup>
import {ref} from 'vue';

import IssueHeader from './components/IssueHeader.vue';
import IssueItem from './components/IssueItem.vue';

const newIssue = ref('');

let id = 3;
const issues = ref([
    {
        id: 1,
        title: '로그인 버튼이 동작 안함',
        status: 'open'
    },

    {
        id: 2,
        title: '다크모드 레이아웃 깨짐',
        status: 'closed'
    }
]);

const addIssue = () => {
    issues.value.push({
        id: id++,
        title: newIssue.value,
        status: 'open'
    });

    newIssue.value = '';
}

const delIssue = (id) => {
    issues.value = issues.value.filter(x => x.id !== id);
}
</script>

<template>
    <IssueHeader/>

    <div class="issue-form">
        <h3>New Issue</h3>

        <input type="text" placeholder="Issue Title"
        @keydown.enter="addIssue"
        v-model="newIssue">
        <button @click="addIssue">Add</button>
    </div>

    <div class="issue-filter">
        <h3>Filter</h3>
        <a class="btn active">All</a>
        <a class="btn">Open</a>
        <a class="btn">Closed</a>
    </div>

    <div class="issue-list">
        <h3>Issues</h3>

        <IssueItem class="issue-item" 
            v-for="issue in issues" :key="issue.id"
            :title="issue.title"
            :status="issue.status" />

        <!--<article class="issue-item"
        v-for="issue in issues" :key="issue">
            <h4>{{issue.title}}</h4>
            <span class="status">{{issue.status}}</span>

            <button @click="delIssue(issue.id)">삭제</button>
        </article>-->


    </div>

    <div class="issue-summary">
        <h3>Summary</h3>
    </div>

        
</template>

<style scoped>

.issue-form {
    h3 {
        font-size: 20px;
    }

    input {
        border: 1px solid #aaa;
        height: 40px;
        border-radius: 8px;
    }

    button {
        height: 40px;
        background-color: blue;
        color: white;
        width: 120px;
        border: none;
        border-radius: 8px;
    }
}

.issue-filter {
    h3 {
        font-size: 20px;
        margin: 0;
    }

    .btn {
        display: inline-block;
        width: 90px;
        height: 40px;
        line-height: 40px;
        text-align: center;
        border: 1px solid #aaa;
        background-color: transparent;
        border-radius: 8px;
        margin-right: 16px;
    }
}

.issue-list {
    h3 {
        font-size: 20px;
        margin: 0;
    }
}

.issue-summary {
    h3 {
        font-size: 20px;
        margin: 0;
    }
}

</style>