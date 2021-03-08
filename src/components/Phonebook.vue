<template>
    <div>
    <v-row>
        <v-col md="8" sm="12">
            <ContactsTable :contacts="contacts"/>
        </v-col>
        <v-col>
            <ContactForm @contact-submit="addContact"/>
        </v-col>
    </v-row>
    </div>
</template>

<script>
import ContactForm from "./ContactForm";
import ContactsTable from "./ContactsTable";

export default {
    components: {ContactForm, ContactsTable},
    data () {
        return {
            contacts: []
        }
    },
    mounted() {
        //data that gets mounted straight to DOM when loaded
        const existingContacts = JSON.parse(localStorage.getItem('contacts'));
        this.contacts = existingContacts || []; //if no contacts use an empty array
    },
    methods: {
        addContact(contact) {
            this.contacts.push(contact);
            localStorage.setItem('contacts', JSON.stringify(this.contacts));
        },

    }
}
</script>

<style></style>