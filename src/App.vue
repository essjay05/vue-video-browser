<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
const YT_API_KEY = process.env.VUE_APP_PUBLIC_API

export default {
    name: 'App',
    components: { SearchBar },
    methods: {
        onTermChange(searchTerm) {
            axios.get('https://googleapis.com/youtube/v3/search', {
                params: {
                    key: YT_API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            }).then(response => console.log(response));
        }
    }
};
</script>
