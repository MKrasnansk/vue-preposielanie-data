<template>
    <div class="editor">
        <p>{{ joinedFullName }}</p>
        <p>
            First name: <br />
            <input v-model="firstName" />
        </p>
        <p>
            Last name: <br />
            <input v-model="lastName" />
        </p>
    </div>
</template>

<script>
export default {
    data() {
        const [firstName = "", lastName = ""] = this.fullName.split(" ");
        return {
            firstName,
            lastName,
        };
    },
    props: {
        fullName: {
            type: String,
            required: false,
            default: "",
        },
    },
    watch: {
        fullName() {
            const [firstName = "", lastName = ""] = this.fullName.split(" ");
            this.firstName = firstName;
            this.lastName = lastName;
        },
        joinedFullName() {
            this.$emit("fullNameUpdate", this.joinedFullName);
        },
    },
    computed: {
        joinedFullName() {
            return [this.firstName, this.lastName]
                .filter((imput) => imput !== "")
                .join(" ");
        },
    },
};
</script>

<style>
.editor {
    border: 5px solid black;
    padding: 1em;
}
</style>
