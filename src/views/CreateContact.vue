<template>
    <div class="page">
        <h4>Thêm mới liên hệ</h4>
        <ContactForm :contact="contact" @submit:contact="createContact" />
    </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import contactService from "@/services/contact.service";

export default {
    components: {
        ContactForm,
    },
    data() {
        return {
            contact: {
                name: "",
                email: "",
                address: "",
                phone: "",
                favorite: false,
            },
        };
    },
    methods: {
        async createContact(data) {
            try {
                await contactService.create(data);
                this.$router.push({ name: "contactbook" });
            } catch (error) {
                console.log(error);
            }
        },
    },
};
</script>
