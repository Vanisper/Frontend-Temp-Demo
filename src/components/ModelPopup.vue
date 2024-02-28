<template>
    <teleport to="body">
        <div v-if="show" class="modal">
            <div class="modal-content">
                <div class="modal-header">
                    <span class="close" @click="onClose">x</span>
                    <h2>{{ title }}</h2>
                </div>
                <div class="modal-body">
                    <p>{{ message }}</p>
                </div>
                <div class="modal-footer">
                    <button @click="onConfirm">{{ confirmText }}</button>
                    <button @click="onCancel">{{ cancelText }}</button>
                </div>
            </div>
        </div>
    </teleport>
</template>

<script lang="ts" setup>
import { onMounted, onUnmounted } from 'vue';

const props = defineProps({
    show: Boolean,
    title: String,
    message: String,
    confirmText: String,
    cancelText: String,
});

const emits = defineEmits(['onConfirm', 'onCancel', 'onClose']);


onMounted(() => {
    console.log('ModelPopup mounted', props.show);
});

onUnmounted(() => {
    console.log('ModelPopup unmounted');
});

const onConfirm = () => {
    emits('onConfirm');
};

const onCancel = () => {
    emits('onCancel');
};

const onClose = () => {
    emits('onClose');
};

</script>

<style scoped>
.modal {
    display: block;
    position: fixed;
    z-index: 1;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;
    background-color: rgb(231 229 228 / 0.75);
    transition-property: opacity;
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
    transition-duration: 150ms;
}

.modal-content {
    background-color: #fefefe;
    margin: 15% auto;
    padding: 20px;
    border: 1px solid #888;
    width: 80%;
}

.modal-header {
    padding: 2px 16px;
    background-color: #5cb85c;
    color: white;
}

.modal-body {
    padding: 2px 16px;
}

.modal-footer {
    padding: 2px 16px;
    /* background-color: #5cb85c; */
    color: white;

    display: flex;
    gap: 15px;
}

.close {
    color: white;
    float: right;
    font-size: 28px;
    font-weight: bold;
}

.close:hover,
.close:focus {
    color: #000;
    text-decoration: none;
    cursor: pointer;
}

button {
    background-color: #5cb85c;
    color: white;
    padding: 14px 20px;
    margin: 8px 0;
    border: none;
    cursor: pointer;
    width: 100%;
}

button:hover {
    opacity: 0.8;
}

button:active {
    background-color: #4CAF50;
    box-shadow: 0 5px #666;
}
</style>