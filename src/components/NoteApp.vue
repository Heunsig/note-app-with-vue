<script setup>
import { ref } from 'vue';

const notes = ref([]);

function addNewNote() {
  const inputEle = document.querySelector('[data-input]');
  const inputValue = inputEle.value;

  if (inputValue === '') {
    return;
  }

  notes.value.push(inputValue);

  inputEle.value = '';
  inputEle.focus();
}
</script>

<template>
  <div class="note-container">
    <h1 class="note-header">Note App (Vue)</h1>
    <!-- Form 섹션 -->
    <section class="note-section">
      <form 
        class="note-form"
        @submit.prevent="addNewNote()"
      >
        <input 
          class="form-control note-form__input" 
          type="text" 
          placeholder="Write task..."
          data-input
        >
        <button 
          type="submit"
          class="btn btn-primary note-form__submit"
        >Add</button>
      </form>
    </section>
    <!-- /Form 섹션 -->

    <!-- Note 리스트 섹션 -->
    <section>
      <div class="note-counter">
        <span>{{ notes.length }}</span>개의 메모가 있습니다.
      </div>
      <ul class="note-list">
        <li 
          class="note-item"
          v-for="note in notes"
        >
          {{ note }}
        </li>
      </ul>
    </section>
    <!-- /Note 리스트 섹션 -->
  </div>
</template>

<style>
.note-container {
	padding: 1rem .5rem;
	width: clamp(12.5rem, 100%, 25rem);
	margin: 0 auto;
}

.note-header {
	font-size: 1.5rem;
	margin-bottom: 1rem;
}

.note-section {
	margin-bottom: 1rem;
}

.note-form {
	display: flex;
	gap: 0.5rem;
}

.note-form__input {
	flex: 1;
}

.note-counter {
	display: flex;
	justify-content:flex-end;
}

.note-list {
	list-style: none;
	padding: 0.5rem 0;
	margin: 0;
}

.note-item {
	display: flex;
	align-items: center;
	gap: .5rem;
	padding: .5rem 0;
}

.note-item:not(:last-child) {
	border-bottom: 1px solid #ccc;
}
</style>