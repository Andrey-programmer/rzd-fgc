<template>
    <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12>
            <v-card class="elevation-12">
                <v-toolbar dark color="primary">
                  <v-toolbar-title>Форма заказа</v-toolbar-title>               
                </v-toolbar>
                <v-card-text>
                    <v-form ref="form" v-model="valid" lazy-validation>
                        <v-text-field 
                          v-for="(field, index) in form"
                          :key="field.id"
                           name="email"
                          :label="field.name"
                          :type="field.type"
                          :rules="field.validate === 'string' ? string : field.validate === 'num'? num: req"
                          :code="field.code"
                          :parent="field.parent"
                          :orderID="field.orderID"
                          v-model="values[index]"
                        >
                        </v-text-field>
                    </v-form>
                </v-card-text>
                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn 
                    color="primary" 
                    @click="onSubmit"
                    :disabled="!valid"
                    >Отправить заказ</v-btn>
                </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
    export default {
    data () {
        return {
            values: [

            ],
            valid: false,
            req: [
                v => !!v || 'Поле не должно быть пустым'
            ],
            num: [
                v => !!v || 'Поле не должно быть пустым',
                v => /^[0-9]+$/.test(v) || 'Поле должно быть числом'
            ],
            string: [
                v => !!v || 'Поле не должно быть пустым',
                v => /^[a-zа-яё]+$/i.test(v) || 'Поле должно быть строкой'
            ]
        }
    },

    computed: {
        form() {
            this.$store.getters.form.forEach(element => {
                this.values.push(element.val)
            });
            return this.$store.getters.form
        }
    },
    methods: {
        onSubmit() {
            if (this.$refs.form.validate()) {
               /* Отправляю данные */
            }
        }
    },
}
</script>

<style lang="scss" scoped>

</style>