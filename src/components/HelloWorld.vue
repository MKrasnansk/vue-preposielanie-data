<template>
    <div class="hello">
        <full-name-editor
            :fullName="fullName"
            v-on:fullNameUpdate="fullNameUpdate"
        />
        <p>
            Full name: <br />
            {{ fullName }} <br />
            <input v-model="fullName" />
        </p>
    </div>
</template>

<script>
import FullNameEditor from "./fullNameEditor.vue";

export default {
    components: {
        FullNameEditor,
    },
    data() {
        return {
            fullName: "",
        };
    },
    methods: {
        fullNameUpdate(newFullName) {
            this.fullName = newFullName;
        },
    },
};
</script>

<style scoped>
p {
    font-size: 1.3em;
    line-height: 3em;
    margin: 0.5em;
}
input {
    font-size: 2em;
    padding: 0.5em;
}
</style>
