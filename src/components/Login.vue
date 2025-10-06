<template>
    <div class="container">
        <div class="row">
            <div class="col">
                <h1 class="mt-5">Login</h1>
                <hr />
                <form-tag
                    @myevent="submitHandler"
                    name="myform"
                    event="myevent"
                >
                    <text-input
                        v-model="email"
                        label="Email"
                        type="email"
                        name="email"
                        required="true"
                    ></text-input>

                    <text-input
                        v-model="password"
                        label="Password"
                        type="password"
                        name="password"
                        required="true"
                    ></text-input>
                    <input
                        type="submit"
                        class="btn btn-primary"
                        value="Login"
                    />
                </form-tag>
            </div>
        </div>
    </div>
</template>

<script>
import FormTag from "./forms/FormTag.vue";
import TextInput from "./forms/TextInput.vue";

export default {
    name: "AppLogin",
    components: { TextInput, FormTag },
    data() {
        return {
            email: "",
            password: "",
        };
    },
    methods: {
        submitHandler() {
            console.log("Form submitted");

            const payload = {
                email: this.email,
                password: this.password,
            };

            const requestOptions = {
                method: "POST",
                body: JSON.stringify(payload),
            };

            fetch("http://127.0.0.1:8081/users/login", requestOptions)
                .then((response) => response.json())
                .then((data) => {
                    if (data.error) {
                        console.error("Error:", data.message);
                    } else {
                        console.log("Success: ", data);
                    }
                })
                .catch((error) => {
                    console.error("Error:", error);
                });
        },
    },
};
</script>

<style>
</style>