<template>
  <div class="container">
    <logo class="title" />
    <div class="checkboxes">
      <label>
        <input type="checkbox" v-model="arabicLetters" />
        حروف عربی
        <span class="desc">ي ك</span>
      </label>
      <label>
        <input type="checkbox" v-model="arabicNumbers" />
        اعداد عربی
        <span class="desc">٤ ٥ ٦</span>
      </label>
      <label>
        <input type="checkbox" v-model="englishNumbers" />
        اعداد انگلیسی
        <span class="desc">1 2 3 4 5 6 7 8 9 0</span>
      </label>
      <label>
        <input type="checkbox" v-model="englishPunctuation" />
        علایم انگلیسی
        <span class="desc">? , " "</span>
      </label>
      <label>
        <input type="checkbox" v-model="punctuationSpace" />
        حذف فاصله قبل از علایم نگارشی
      </label>
      <label>
        <input type="checkbox" v-model="extraSpace" />
        فاصله اضافه بین کلمات
      </label>
    </div>
    <textarea
      name="persian-text"
      spellcheck="false"
      cols="100"
      rows="10"
      v-model="persianText"
      id="persian-text"
    ></textarea>
    <div id="corrected" v-html="persianTextCorrected"></div>
  </div>
</template>

<script>
import Logo from "~/components/Logo.vue";

export default {
  components: {
    Logo
  },
  data() {
    return {
      persianText: `مي دانست ؟ كه با زنده نگه داشتن زبان ويژه يك ملت ، در واقع آن ملت ! را زندگي و جاودانگي بخشيده است .
اعداد عربی ٤ ٥ ٦
اعداد انگیسی 1 2 3 4 5 6 7 8 9 0
علایم, انگلیسی? برای مثال استفاده از "نقل قول".
در متنی که فاصله      اضافه   داشته باشد.`,
      persianTextCorrected: "",
      arabicLetters: true,
      arabicNumbers: true,
      englishNumbers: true,
      englishPunctuation: true,
      punctuationSpace: true,
      extraSpace: true
    };
  },
  methods: {
    replace() {
      let text = this.persianText;

      text = text.replace(/\n/g, "<br />");

      if (this.arabicLetters === true) {
        text = text.replace(/ي/g, "ی");
        text = text.replace(/ك/g, "ک");
        this.persianTextCorrected = text;
      }

      if (this.arabicNumbers === true) {
        text = text.replace(/٤/g, "۴");
        text = text.replace(/٥/g, "۵");
        text = text.replace(/٦/g, "۶");
        this.persianTextCorrected = text;
      }

      if (this.englishNumbers === true) {
        text = text.replace(/1/g, "۱");
        text = text.replace(/2/g, "۲");
        text = text.replace(/3/g, "۳");
        text = text.replace(/4/g, "۴");
        text = text.replace(/5/g, "۵");
        text = text.replace(/6/g, "۶");
        text = text.replace(/7/g, "۷");
        text = text.replace(/8/g, "۸");
        text = text.replace(/9/g, "۹");
        text = text.replace(/0/g, "۰");
        this.persianTextCorrected = text;
      }

      if (this.englishPunctuation === true) {
        text = text.replace(/\?/g, "؟");
        text = text.replace(/\,/g, "،");
        text = text.replace(/ \"/g, "«");
        text = text.replace(/\" /g, "» ");
        text = text.replace(/\"/g, "»");
        text = text.replace(/\"\S/g, x => {
          return "»" + x.replace('"', "");
        });
      }

      if (this.punctuationSpace === true) {
        text = text.replace(/ \،/g, "،");
        text = text.replace(/ \./g, ".");
        text = text.replace(/ \!/g, "!");
        text = text.replace(/ \؟/g, "؟");
      }

      if (this.extraSpace === true) {
        text = text.replace(/. ./g, x => {
          return x.replace("  ", " ");
        });
      }

      this.persianTextCorrected = text;
    }
  },
  computed: {
    all() {
      return (
        this.persianText,
        this.arabicLetters,
        this.arabicNumbers,
        this.englishNumbers,
        this.englishPunctuation,
        this.punctuationSpace,
        this.extraSpace,
        Date.now()
      );
    }
  },
  watch: {
    all() {
      this.replace();
    }
  }
};
</script>
