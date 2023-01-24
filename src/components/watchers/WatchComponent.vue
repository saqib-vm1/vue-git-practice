<template>
    <h2>Watch Method Component</h2>
    <p>Watchers are used to execute some code on specified reactive state changes.</p>
    <p>Watchers allows us to perform side effects in reaction to state changes.</p>
    <div>
        <label>Enter User Id</label>
        <input v-model="userId" />
    </div>
    <div>
        <span v-if="errorMessage !== ''">{{ errorMessage }}</span>
        <div v-if="errorMessage === ''">
            User Name: {{ userInfo.name }} - User Age: {{ userInfo.age }}
        </div>
    </div>
</template>

<script setup>
    import { ref, watch } from 'vue';
    import { dummyUsers } from './dummyUsers.js';

    const userId = ref('');
    const userInfo = ref({});
    const errorMessage = ref('');

    watch(userId, async () => {
        userInfo.value = {}
        const userDetails = await new Promise((resolve) => {
            setTimeout(() => {
                if(dummyUsers[userId.value]) {
                    resolve(dummyUsers[userId.value]);
                } else {
                    resolve({errorMessage: 'No user for this Id.'})
                }
            }, 1500)
        });

        if(userDetails.errorMessage) {
            errorMessage.value = userDetails.errorMessage;
        } else {
            userInfo.value = userDetails;
        }
    })
</script>

<!-- In Watch method we can call asynchronous functions -->
<!-- watch's first argument can be different types of 
    reactive "sources": it can be a ref (including computed refs),
    a reactive object, a getter function, or an array of multiple sources: -->

<!-- When we call watch() directly on a reactive object, 
    it will implicitly create a deep watcher - 
    the callback will be triggered on all nested mutations: -->