<template>
  <modal :name="NEW_POLL_OPTION_MODAL_ID" :height="'auto'" :maxHeight="600">
    <div class="new-profile-item__container">
      <div class="new-profile-item-modal__header">
        <img
          class="new-profile-item-modal__header__icon"
          src="../../../../../media/images/icon.ico"
        >
        <div class="new-profile-item-modal__header__title">{{ $t('Add to Options') }}</div>
      </div>
      <validated-form ref="modalForm" class="new-profile-item-modal__body">
        <div class="row">
          <div class="small-7 columns">
            <VFormGroup :title="$t('Option')" :metadata="metaData.name" v-model="option.name"/>
          </div>
          <div class="small-5 columns">
            <div class="flex flex--center">
              <span class="command-span">{{ $t(baseCommand) }}</span>
              <VFormGroup
                :title="$t('Command')"
                v-model="option.parameter"
                :metadata="metaData.parameter"
              />
            </div>
          </div>
        </div>
      </validated-form>
      <div class="new-profile-item-modal__controls">
        <button
          class="button button--default"
          @click="onCancelNewItemModalHandler"
        >{{ $t('Cancel') }}</button>
        <button
          class="button button--action"
          @click="onAddNewItemHandler"
          :disabled="errors.items.length > 0"
        >{{ $t('Done') }}</button>
      </div>
    </div>
  </modal>
</template>
<script lang="ts" src="./ChatbotPollOptionModal.vue.ts"></script>

<style lang="less" scoped>
@import '../../../../styles/index';
.new-profile-item-modal__header {
  display: flex;
  flex-direction: row;
  align-items: center;
  height: 30px;
  border-bottom: 1px solid var(--border);

  .new-profile-item-modal__header__icon {
    padding-left: 10px;
    width: 32px;
  }

  .new-profile-item-modal__header__title {
    .text-transform();
    flex-grow: 1;
    .padding-left();
  }
}

.command-span {
  .margin-right();
}

.new-profile-item-modal__body {
  .padding--20();
}

.new-profile-item-modal__controls {
  background-color: var(--section);
  border-top: 1px solid var(--border);
  padding: 8px 16px;
  text-align: right;
  flex-shrink: 0;
  z-index: 10;

  .button {
    margin-left: 8px;
  }
}
</style>
