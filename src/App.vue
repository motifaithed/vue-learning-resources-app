<template>
    <ul>
        <li v-for="resource in storedResources" :key="resource.id">{{ resource.title }}</li>
    </ul>
</template>
<script>
    export default {
        data(){
            return {
                storedResources:[
                    {
                        id: 'official-guide',
                        title: 'Official Guide',
                        description: 'Official vue guide docs',
                        link: 'https://vuejs.org'
                    },
                    {
                        id: 'google',
                        title: 'Google',
                        description: 'search everything',
                        link: 'https://www.google.com'
                    }
                ]
            }
        }
    }
</script>