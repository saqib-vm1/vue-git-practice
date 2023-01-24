<template>
    <h1>WatchEffect Component</h1>
    <p>watchEffect automatically track the callback's reactive dependencies.</p>
    <p>there is no need to specify <code>immidiate: true</code>to execute callback on mount.</p>
    <input v-model="userId" />
    <div v-if="errorMessage !== ''">{{ errorMessage }}</div>
    <div v-if="errorMessage === ''">User Name: {{ userInfo.name }} - Age: {{ userInfo.age }}</div>
</template>

<script setup>
    import { ref, watchEffect } from 'vue';
    import { dummyUsers } from './dummyUsers';

    const userId = ref('1');
    const userInfo = ref({});
    const errorMessage = ref('');

    watchEffect(async () => {
        // userId.value;
        userInfo.value = {};
        errorMessage.value = '';
        const userDetails = await new Promise((resolve) => {
            setTimeout(() => {
                if(dummyUsers[userId.value]) {
                    resolve(dummyUsers[userId.value]);
                } else {
                    resolve({errorMessage: 'No user with such Id'});
                }
            }, 1500)
        })

        if(userDetails.errorMessage) {
            errorMessage.value = userDetails.errorMessage;
        } else {
            userInfo.value = userDetails;
        }
    })
</script>

<!-- watchEffect only tracks dependencies during its synchronous execution. 
    When using it with an async callback, only properties accessed before 
    the first await tick will be tracked. -->