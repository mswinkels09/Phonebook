<template>
    <div>
        <h2> New Contact</h2>
        <v-form @submit.prevent="handleSubmit" ref="contactForm" class="mt-2 mr-3" > 
            <v-text-field outlined :rules="validators.firstName" label="First Name" v-model="form.firstName"></v-text-field>
            <v-text-field outlined :rules="validators.lastName" label="Last Name" v-model="form.lastName"></v-text-field>
            <v-text-field outlined :rules="validators.phone" label="Phone" v-model="form.phone"></v-text-field>
            <v-select outlined  :items="options" label="Phone Type" v-model="form.type"></v-select>
            <v-text-field outlined :rules="validators.email" label="Email" v-model="form.email"></v-text-field>
            <v-btn type="submit" color="primary" dark>Submit</v-btn>
        </v-form>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                form: {
                    firstName: "",
                    lastName: "",
                    phone: "",
                    type: "",
                    email: "",
                },
                options: ["Home", "Office", "Cell"],
                validators: {
                    firstName: [
                        val => !!val || "Contact first name is required",
                        val => val.length < 25 || "first name must be less than 25 characters"
                    ],
                    lastName: [
                        val => val.length < 25 || "first name must be less than 25 characters"
                    ],
                    phone: [
                        val => val.length === 10 || "Enter valid phone number"
                    ],
                    email: [
                        val => val.includes('@') || "Enter valid email"
                    ]
                }
            }
        },
        methods: {
            handleSubmit() {
                //check validity
                const isValid = this.$refs.contactForm.validate();

                if(!isValid) {
                    return;
                };
                this.$emit("contact-submit", this.form);
                this.form = {
                    firstName: "",
                    lastName: "",
                    phone: "",
                    type: "",
                    email: ""
                };

                this.$refs.contactForm.resetValidation();
            }
    }
    }
</script>

<style></style>