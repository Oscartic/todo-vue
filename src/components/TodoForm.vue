<template>
    <div>
        <b-form @submit.prevent="$emit('processTodo', todo)">
            <b-form-group
                id="todo"
                label="todo"
                label-for="todo"
            >
                <b-form-input
                    autocomplete="off"
                    id="todo"
                    v-model="todo.text"
                    :state="!$v.todo.text.$invalid"
                    placeholder="Introduce Tarea"
                    @input="$v.todo.$touch"
                ></b-form-input>
                <b-form-invalid-feedback id="todoInfo" v-if="$v.todo.$dirty">
                    Este campo es requerido y debe tener una longitud minima de 4 caracteres
                </b-form-invalid-feedback>
            </b-form-group>

            <b-button 
                type="submit" 
                variant="primary" 
                :disabled="$v.todo.$invalid"
            >
                {{ todoSubmit }}
            </b-button>
        </b-form>
    </div>
</template>

<script>
    import { validationMixin } from 'vuelidate'
    import { required, minLength } from 'vuelidate/lib/validators'

    export default {

        mixins: [validationMixin],

        props: {
            todo: {
                type: Object,
                required: true
            },
            todoSubmit: {
                type: String,
                default: 'Crear Todo'
            }
        },
        validations: {
            todo: {
                text: {
                    required, minLength: minLength(4)
                }
            }
        }   
    }
</script>