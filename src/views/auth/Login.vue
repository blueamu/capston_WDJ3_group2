/*로그인 페이지*/

<template>
    <v-layout>
        <v-card-text class="pa-4">
            <v-container class="d-flex" style="margin-top: 50px;">
                <v-layout>
                    <v-flex style="width:500px;" xs12 sm12 md12>
                        <v-img src="/static/fogg-welcome-2.png" class="ma-5 pa-4"></v-img>
                    </v-flex>
                </v-layout>
                <span class="text-xs-left text-md-left">
                <v-layout row wrap>
                    <v-flex xs12 sm12 md12>
                        <v-form v-model="valid">
                            <v-flex>
                                <h1 class="green--text font-weight-bold" style="text-align: center; margin-bottom: 40px;">LOGIN</h1>
                            <v-text-field 
                                name="email" label="email" class="email login-input"
                                type="email" v-model="email" :rules="emailRules"
                                requited>
                            </v-text-field>
                    
                            <v-text-field
                                name="password" label="password" class="password login-input"
                                if="password" type="password" v-model="password" :rules="passwordRules"
                                required>
                            </v-text-field>
                            
                            <v-card-actions>
                            <v-btn
                            type="submit" block text 
                            class="success" style="margin-top: 20px; margin-bottom: 20px;" form="check_login">
                            <!-- block flat -->
                            LOGIN
                            </v-btn>
                            </v-card-actions>
                            <v-card-actions>
                                <v-btn
                                class="green--text" style="background-color: lightgray;" block outlined
                                @click="signupPage">
                                SIGNUP
                                </v-btn>
                            </v-card-actions>
                            </v-flex>
                        </v-form>
                    </v-flex>
                </v-layout>
                </span>
                
                <v-card-actions>
                    <v-btn color="error" v-if="error" block flat >
                        <span>{{ error }}</span>
                    </v-btn>
                </v-card-actions>
            </v-container>
        </v-card-text>
    </v-layout>
</template>

<script>
export default {
    name: 'Login',
    data(){
        return{
    valid: false,
    email:'',
    emailRules:[
        v => !!v || '이메일을 입력해 주세요!',
        v => /.+@.+/.test(v) || '메일 형식으로 입력해 주세요!'
    ],

    password:'',
    passwordRules:[
        v => !!v || '패스워드를 입력해 주세요!',
        v => v.length >= 6 || '6글자이상 입력해 주세요!'
    ],
    error:null, //에러 메세지

                }
    },

    methods: {
        signupPage(){
            this.$router.push({name: 'signup'})
            this.$store.state.isLoginDialog=false
        },
    }
}
</script>

<style scoped>

.login-input{
    margin-left: 20px;
    width:500px;
    margin-bottom:20px;
}
</style>