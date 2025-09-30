<template>
    <div class="form-check">
        <input
            class="form-check-input"
            type="checkbox"
            :checked="checked"
            :name="name"
            :value="value"
            :required="required"
        />
        <label class="form-check-label" :for="name">
            {{ label }}
        </label>
    </div>
</template>

<script>
export default {
    name: "CheckInput",
    props: ["label", "required", "name", "value", "checked"],
};
</script>

<style>
</style>