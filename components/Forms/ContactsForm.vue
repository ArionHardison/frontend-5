<template>
    <form v-on:submit.prevent="submitForm" method="post" action="form.php" id="cf-1" class="contact-form">
        <div class="form-group form-group-xs form-lg-no-space">
            <p class="input-group gutter-width-xs no-space">
                <span class="gutter-width">
                    <input v-model="form.name" name="cf-1-name" type="text" class="font-size-lg pt-0" id="cf-1-name" placeholder="Name" required="required">
                </span>

                <span class="gutter-width">
                    <input v-model="form.email" name="cf-1-email" type="email" class="font-size-lg pt-0" id="cf-1-email" placeholder="Email" required="required">
                </span>
            </p>
        </div>

        <div class="form-group form-group-xs form-lg-no-space">
            <p class="input-group gutter-width-xs no-space">
                <span class="gutter-width">
                    <input v-model="form.phone" name="cf-1-phone" type="text" class="font-size-lg pt-0" id="cf-1-phone" placeholder="Phone no." required="required">
                </span>

                <span class="gutter-width">
                    <input v-model="form.subject" name="cf-1-subject" type="text" class="font-size-lg pt-0" id="cf-1-subject" placeholder="Subject" required="required">
                </span>
            </p>
        </div>

        <div class="form-group form-group-xs form-lg-no-space">
            <textarea v-model="form.message" name="cf-1-message" class="font-size-lg pt-0" id="cf-1-message" placeholder="Message" required="required"></textarea>
        </div>

        <div class="form-group form-group-xs">
            <button type="submit" class="btn btn-gradient">Send</button>
        </div>

        <transition appear leave-active-class="animated fadeOut">
            <div v-if="callAlert" id="alert" :class="'animated fadeIn alert alert--shadow alert-' + alertClass">
                {{ responseMessage }}
            </div>
        </transition>
    </form>
</template>

<script>
    import axios from 'axios';

    export default {
        name: 'ContactsForm',
        data() {
            return {
                form: {
                    name: '',
                    email: '',
                    phone: '',
                    subject: '',
                    message: ''
                },
                successMessage: "Sender's message was sent successfully",
                warningMessage: 'Fill up the form, please!',
                errorMessage: 'Something go wrong. Try again later!',
                responseMessage: '',
                alertClass: '',
                callAlert: false
            }
        },
        methods: {
            async submitForm() {
                axios.post( 'https://store.adveits.com/API/form.php', this.form, {
                    headers: {
                        'Access-Control-Allow-Origin': '*',
                        'Content-Type': 'application/json; charset=UTF-8'
                    },
                }, ).then( response => {
                    if ( response.data.status === 'success' ) {
                        this.responseMessage = this.successMessage;
                    }

                    if ( response.data.status === 'warning' ) {
                        this.responseMessage = this.warningMessage;
                    }

                    if ( response.data.status === 'error' ) {
                        this.responseMessage = this.errorMessage;
                    }
                    this.alertClass = response.data.status;
                    this.callAlert  = true;

                    setTimeout( () => {
                        this.callAlert = false;
                    }, 2000 )
                } ).catch( error => {
                    this.responseMessage = this.errorMessage;
                    this.alertClass      = 'danger';
                    this.callAlert       = true;

                    setTimeout( () => {
                        this.callAlert = false;
                    }, 2000 )
                } );
            }
        }
    }
</script>
