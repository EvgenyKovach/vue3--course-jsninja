<template>
    <div class="auth-page">
        <div class="container">
            <Form class="flex flex-col mt-3">
                <FormField 
                    name="username">
                        <FormItem class="flex flex-col justify-center">
                            <FormLabel>Username</FormLabel>
                            <FormControl>
                                <Input class="border-1 p-1" placeholder="USERNAME" :value.sync="login"/>
                                <input class="border-1 p-1" placeholder="USERNAME" v-model="login"/>
                            </FormControl>
                            <FormMessage />
                    </FormItem>
                </FormField>
                <FormField 
                    name="pass">
                        <FormItem class="flex flex-col justify-center">
                            <FormLabel>Pass</FormLabel>
                            <FormControl>
                                <Input class="border-1 p-1" placeholder="Pass" v-model="pass"/>
                            </FormControl>
                            <FormMessage />
                    </FormItem>
                </FormField>
            </Form>
            {{ login }}
        </div>
    </div>
</template>
<script setup lang="ts">
import { toTypedSchema } from '@vee-validate/zod'
import * as z from 'zod'
import { ref} from 'vue';
const props = defineProps<{
  title?: String;
}>()

const login = ref<String>('');
const pass = ref<String>('');

const formSchema = toTypedSchema(z.object({
  username: z.string().min(2).max(50),
  pass: z.string().min(2).max(50),
}))

const form = useForm({
  validationSchema: formSchema,
})

const onSubmit = form.handleSubmit((values) => {
  console.log('Form submitted!', values)
})
</script>