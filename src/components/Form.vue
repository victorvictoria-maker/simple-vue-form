<template lang="en">
<h1>Simple Sign Up Form</h1>

<p>
    <span v-for="(item, i) in errors" :key="i" id="items">{{item}}, </span>
    <span :class="{display:show}">is invalid.</span>
</p>

<form action="" method="post">
    <label for="name">Name: </label>
    <input type="name" name="name" id="name" placeholder="Name" v-model="form.name">
    <br> <br>

    <label for="email">Email: </label>
    <input type="email" name="email" id="email" placeholder="Email" v-model="form.email">
    <br> <br>

    <label for="gender">Gender: </label>
    <input type="radio" name="gender" id="male" value="male" v-model="form.gender">Male
    <input type="radio" name="gender" id="female" value="female" v-model="form.gender">Female
    <br> <br>

    <label for="country">Country: </label>
    <select name="country" id="country" v-model="form.country">
        <option value="Nigeria">Nigeria</option>
        <option value="USA">USA</option>
        <option value="UK">UK</option>
        <option value="Spain">Spain</option>
        <option value="Ghana">Ghana</option>
    </select>
    <br> <br>

    <label for="stack">Stack: </label>
    <input type="checkbox" name="stack" id="javascript" value="javascript" v-model="form.stack">Javascript
    <input type="checkbox" name="stack" id="php" value="php" v-model="form.stack">Php
    <input type="checkbox" name="stack" id="python" value="python" v-model="form.stack">Python
    <input type="checkbox" name="stack" id="c++" value="c++" v-model="form.stack">C++
    <br> <br>

    <button @click.prevent="signUp">Sign Up</button>
</form>
</template>

<script>
export default {
    name: "FormComponent",
    data() {
        return {
            show: true,
            form: {
                name: "",
                email: "",
                gender: "",
                country: "",
                stack: []
            },
            errors: []
        }
    },
    methods: {
        signUp() {
            this.errors = [];

            for (let item in this.form) {
                if (this.form[item] === "" || this.form[item].length === 0) {
                    this.errors.push(item);
                    this.show = false;
                }
            }

            if (this.errors.length === 0) {
                alert('Data submitted successfully');
                this.show = true;
                this.form.name = "";
                this.form.email = "";
                this.form.gender = "";
                this.form.country = "";
                this.form.stack = [];
            }

        }
    },
}
</script>

<style scoped>
#items {
    text-transform: capitalize;
}

.display {
    display: none;
}
</style>
