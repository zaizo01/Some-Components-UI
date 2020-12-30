<template>
    <div class="mt-5">
        <h1>Forms</h1>
        <b-row>
            <b-col cols="3">
                <b-form-input type="text" placeholder="Enter your name..." :state="info" v-model="text"></b-form-input>
                <small v-if="!info">Min 3 characteres</small>
                <p>Text: {{text}}</p>
            </b-col>
            <b-col cols="3">
                  <b-form-select v-model="select" :options="animals"></b-form-select>
                  <p>Selected: {{select}}</p>
            </b-col>
            <b-col cols="3">
                <b-form-radio-group v-model="radio" :options="animalsRadio"></b-form-radio-group>
                <p>Radio Selected: {{radio}}</p>
            </b-col>
            <b-col cols="3">
                <b-form-checkbox-group v-model="check" :options="animalsRadio"></b-form-checkbox-group>
                <p>Checked: {{check}}</p>
            </b-col>
        </b-row>
    </div>
</template>

<script>
export default {
    name: 'Forms',
    data() {
        return {
        text: '',
        select: null,
        radio: null,
        check: [],
        animals: [
            {value: null, text: 'Select animals'},
            {value: 'Dog', text: 'Wau Wau'},
            {value: 'Cat', text: 'Miau Miau'},
            {value: 'Duck', text: 'Cloack'}
        ],       
        animalsRadio: [
            {value: 'Dog', text: 'Wau Wau'},
            {value: 'Cat', text: 'Miau Miau'},
            {value: 'Duck', text: 'Cloack'}
        ]       
        }
    },
    computed: {
        info(){
            return this.text.length > 2 ? true : false;
        }
    },
}
</script>