<script setup lang="ts">
import { ref } from "vue"
import { marked } from "marked"
import { LangDevsAppendix, LangDevsTowerImageURL } from "../../content"
import SceneContent from "../common/SceneContent.vue"
import SceneVisibilityChecker from "../common/SceneVisibilityChecker.vue"

import { useI18n } from "vue-i18n"
import type { MessageSchema, NumberSchema } from "../../locales/schema"
const { t } = useI18n<{ message: MessageSchema; number: NumberSchema }>({
  useScope: "global"
})
const vis = ref(false)
</script>

<template>
  <section id="scene-developers" class="section-wrap">
    <div class="container">
      <Transition name="fade">
        <div v-if="vis">
          <div class="img-wrap">
            <img :src="LangDevsTowerImageURL" :alt="t('ArtworkDescription')" />
          </div>
          <div class="scene-arrow">
            <img src="/icons/arrow.svg" alt="" />
            <p v-html="marked.parse(t('Devs.TowerJoke'))" />
          </div>
        </div>
      </Transition>

      <div class="content">
        <SceneContent
          :tag="'Devs.Tag'"
          :title="'Devs.Title'"
          :text="'Devs.Text'"
          @visible="vis = true"
        >
          <div class="brand-grid">
            <div class="brand-item">
              <div>
                <div class="icon-wrap">
                  <img
                    src="/brands/vscode.svg"
                    alt="Visual Studio Code logo blur"
                    loading="lazy"
                  />
                  <img
                    src="/brands/vscode.svg"
                    alt="Visual Studio Code logo"
                    loading="lazy"
                  />
                </div>
              </div>
              <p>{{ t("Devs.BoxOne") }}</p>
            </div>

            <div class="brand-item">
              <div>
                <div class="icon-wrap">
                  <img src="/brands/ptyxis.svg" alt="Ptyxis logo blur" />
                  <img src="/brands/ptyxis.svg" alt="Ptyxis logo" />
                </div>
              </div>
              <p>{{ t("Devs.BoxTwo") }}</p>
            </div>

            <div class="brand-item">
              <div>
                <div class="icon-wrap">
                  <img
                    src="/brands/devpod.svg"
                    alt="Devpod logo blur"
                    loading="lazy"
                  />
                  <img
                    src="/brands/devpod.svg"
                    alt="Devpod logo"
                    loading="lazy"
                  />
                </div>
              </div>
              <p>{{ t("Devs.BoxThree") }}</p>
            </div>

            <div class="brand-item">
              <div>
                <div class="icon-wrap">
                  <img
                    src="/brands/homebrew.svg"
                    alt="Homebrew logo blur"
                    loading="lazy"
                  />
                  <img
                    src="/brands/homebrew.svg"
                    alt="Homebrew logo"
                    loading="lazy"
                  />
                </div>
              </div>
              <p>{{ t("Devs.BoxFour") }}</p>
            </div>
          </div>

          <div
            v-if="LangDevsAppendix"
            v-html="marked.parse(t('Devs.Appendix'))"
          />
        </SceneContent>
      </div>
    </div>
    <SceneVisibilityChecker name="#scene-developers" />
  </section>
</template>
