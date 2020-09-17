<template>
  <ft-card
    class="relative card"
  >
    <h3>
      {{ $t("Settings.Sync Settings.Sync Settings") }}
    </h3>
    <div class="switchColumnGrid">
      <div class="switchColumn">
        <ft-toggle-switch
          :label="$t('Settings.Sync Settings.Synchronize Subscriptions')"
          :default-value="syncSubscriptions"
          @change="handleSyncSubscriptionsChange"
        />
        <ft-toggle-switch
          :label="$t('Settings.Sync Settings.Synchronize History')"
          :default-value="syncHistory"
          @change="handleSyncHistoryChange"
        />
      </div>
      <div class="switchColumn">
        <ft-toggle-switch
          :label="$t('Settings.Sync Settings.Synchronize Settings')"
          :default-value="syncSettings"
          @change="handleSyncSettingsChange"
        />
        <ft-toggle-switch
          :label="$t('Settings.Sync Settings.Synchronize Preferences')"
          :default-value="syncPreferences"
          @change="handleSyncPreferencesChange"
        />
      </div>
    </div>
    <br>

    <div class="switchGrid">
      <ft-input
        :placeholder="$t('Settings.Sync Settings.WebDAV.WebDAV Server URL')"
        :show-arrow="false"
        :show-label="true"
        :value="webdavServerUrl"
        @input="handleWebdavServerUrlInput"
      />
      <ft-input
        :placeholder="$t('Settings.Sync Settings.WebDAV.WebDAV Server Directory')"
        :show-arrow="false"
        :show-label="true"
        :value="webdavServerDir"
        @input="handleWebdavServerDirInput"
      />
      <ft-input
        :placeholder="$t('Settings.Sync Settings.WebDAV.WebDAV Username')"
        :show-arrow="false"
        :show-label="true"
        :value="webdavUsername"
        @input="handleWebdavUsernameInput"
      />
      <ft-input
        :placeholder="$t('Settings.Sync Settings.WebDAV.WebDAV Password')"
        :show-arrow="false"
        :show-label="true"
        :value="webdavPassword"
        @input="handleWebdavPasswordInput"
      />
      <ft-toggle-switch
        :label="$t('Settings.Sync Settings.WebDAV.Use WebDAV Digest Authentication')"
        :default-value="webdavDigestAuth"
        @change="updateWebdavDigestAuth"
      />
      <ft-select
        :placeholder="$t('Settings.Sync Settings.Sync Strategy.Sync Strategy')"
        :value="syncStrategy"
        :select-names="syncStrategyNames"
        :select-values="syncStrategyValues"
        @change="updateSyncStrategy"
      />
    </div>
    <br>
    <!-- Auto Sync is not implemented yet -->
    <!--
    <ft-flex-box>
      <ft-toggle-switch
        :label="$t('Settings.Sync Settings.Auto Sync')"
        :default-value="autoSync"
        @change="updateAutoSync"
      />
    </ft-flex-box>
    <br>
    -->
    <ft-flex-box>
      <ft-button
        :label="$t('Settings.Sync Settings.Synchronize Now')"
        text-color="var(--text-with-main-color)"
        background-color="var(--primary-color)"
        @click="handleRestartPrompt"
      />
    </ft-flex-box>
    <ft-prompt
      v-if="showRestartPrompt"
      :label="restartPromptMessage"
      :option-names="restartPromptNames"
      :option-values="restartPromptValues"
      @click="triggerSync"
    />
  </ft-card>
</template>

<script src="./sync-settings.js" />
<style scoped lang="sass" src="./sync-settings.sass" />
