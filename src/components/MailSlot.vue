<script setup>
import { ref } from 'vue'
import appSettings from '@/config/AppSettings';
import emailjs from 'emailjs-com';

const { emailjsServiceId, emailjsTemplateId, emailjsUserId } = appSettings;

const reporter = ref('')
const type = ref('')
const appointment = ref('')

const handleSubmit = () => {
  const templateParams = {
    reporter: reporter.value,
    type: type.value,
    appointment: appointment.value
  };

  emailjs.send(
    emailjsServiceId,
    emailjsTemplateId,
    templateParams,
    emailjsUserId
  )
  .then((response) => {
    console.log('メール送:', response);
    alert('メールが正常に送信されました！');
    reporter.value = '';
    type.value = '';
    appointment.value = '';
  }, (error) => {
    console.error('メール送信失敗:', error);
    alert('メールの送信に失敗しました。もう一度お試しください。');
  });
}
</script>

<template>
  <form @submit.prevent="handleSubmit" class="mail-slot-container">
    <div class="mail-slot">
      <label class="">
        <span>報告者</span>
        <select v-model="reporter">
          <option value="報告者1">報告者1</option>
          <option value="報告者2">報告者2</option>
        </select>
      </label>
      <label>
        <span>入出</span>
        <select v-model="type">
          <option value="入る">入る</option>
          <option value="出る">出る</option>
        </select>
      </label>
      <label>
        <span>アポインター</span>
        <input type="text" v-model="appointment" />
      </label>
    </div>
    <div class="button-container">
      <button type="submit">確認</button>
    </div>
  </form>
</template>

<style scoped>
  .mail-slot-container {
    display: flex;
    flex-direction: column;
  }

  .mail-slot {
    display: flex;
    flex-direction: column;
    border: 1px solid #000000;
    border-radius: 12px;
    padding: 64px 16px;
    width: 600px;
  }

  .mail-slot > label {
    display: flex;
    flex-direction: column;
  }

  .mail-slot > label + label {
    margin-top: 32px;
  }

  .mail-slot > label > span {
    font-size: 24px;
  }

  .mail-slot > label > input, select {
    margin-top: 16px;
    height: 40px;
  }

  .button-container {
    margin: 0 auto;
    margin-top: 32px;
    width: 360px;
  }

  .button-container > button {
    border: 1px solid #000000;
    border-radius: 24px;
    margin: 0 auto;
    width: 360px;
    height: 48px;
    color: #ffffff;
    background-color: #1D4ED8;
  }
</style>