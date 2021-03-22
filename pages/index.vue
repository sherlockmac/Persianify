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
        text = text.replace(/ي/g, "ی").replace(/ك/g, "ک");
      }

      if (this.arabicNumbers === true) {
        text = text
          .replace(/٤/g, "۴")
          .replace(/٥/g, "۵")
          .replace(/٦/g, "۶");
      }

      if (this.englishNumbers === true) {
        text = text
          .replace(/1/g, "۱")
          .replace(/2/g, "۲")
          .replace(/3/g, "۳")
          .replace(/4/g, "۴")
          .replace(/5/g, "۵")
          .replace(/6/g, "۶")
          .replace(/7/g, "۷")
          .replace(/8/g, "۸")
          .replace(/9/g, "۹")
          .replace(/0/g, "۰");
      }

      if (this.englishPunctuation === true) {
        text = text
          .replace(/\?/g, "؟")
          .replace(/\,/g, "،")
          .replace(/ \"/g, "«")
          .replace(/\" /g, "» ")
          .replace(/\"/g, "»")
          .replace(/\"\S/g, x => "»" + x.replace('"', ""));
      }

      if (this.punctuationSpace === true) {
        text = text
          .replace(/ \،/g, "،")
          .replace(/ \./g, ".")
          .replace(/ \!/g, "!")
          .replace(/ \؟/g, "؟");
      }

      if (this.extraSpace === true) {
        text = text.replace(/.\s{2,}./g, x => x.replace(/\s+/, " "));
      }

      this.persianTextCorrected = text;
    }
  },
  updated() {
    this.replace();
  }
};
</script>

