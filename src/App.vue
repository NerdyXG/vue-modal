<template>
    <div class="header">
        <h1>{{ title }}</h1>
        <input type="text" ref="name">
        <button @click="handleClick">Click here</button>
        <br>
        <button @click="modalToggler" style="margin-top: 15px;">Open Modal</button>
        <button @click="contactModalToggler" style="margin-left: 5px;">Contact us</button>
    </div>

    <teleport to=".modals">
        <Modal
            v-show="showModal"
            @close="modalToggler"
            :header="header"
            :text="text"
            :theme="theme"
        >
            <h1>Book Giveaway!</h1>
            <p>Get your dream book for half the price!</p>
            <template v-slot:links>
                <a href="#">Sign up</a>
                <a href="#">Learn more</a>
            </template>
        </Modal>
    </teleport>


    <!-- Modal 2 Challenge - Contact us -->
    <teleport to=".modals">
        <Modal 
            v-show="showContactModal"
            @close="contactModalToggler"
            :theme="theme"
        >
            <h1>Contact us</h1>
            <form action="post">
                <div class="field-container">
                    <!-- <label for="email">Email</label><br> -->
                    <input type="email" name="email" id="email" placeholder="Email" autofocus><br>
                </div>

                <div class="field-container">
                    <!-- <label for="password">Password</label><br> -->
                    <!-- <input type="password" name="password" id="password" placeholder="Password"> -->
                    <textarea name="message" id="message" placeholder="Send us a message"></textarea>
                </div>

                <button type="submit" class="submit-btn"><span class="btn-text">Send</span></button>
            </form>
        </Modal>
    </teleport>
</template>


<script>
import Modal from "./components/Modal.vue"
export default {
    // name: "App",
    components: {Modal},
    data() {
        return {
            title: "My First Vue App :)",
            header: "Sign up for the giveaway!",
            text: "Grab your ninja swag for half the price!",
            theme: "sale",
            showModal: false,
            showContactModal: false
        }
    },
    methods: {
        handleClick() {
            console.log(this.$refs.name.value)
            this.$refs.name.classList.add("value")
            this.$refs.name.focus()
        },

        modalToggler() {
            this.showModal = !this.showModal
        },

        contactModalToggler() {
            this.showContactModal = !this.showContactModal
        }
    }
}
</script>

<style>
    .header {
        text-align: center;
        margin-top: 50px;
    }

    .header input {
        margin-right: 5px;
    }
</style>