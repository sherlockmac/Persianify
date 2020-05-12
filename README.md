# Persianify

> Lets you automate fixing of common Persian text issues, usually made with non-standard keyboards.


<p dir="rtl" style="text-align: right;">
به شما کمک می‌کند تا غلط‌های نگارشی فارسی که معمولا مربوط به صفحه کلید غیراستاندارد است را بصورت خودکار رفع کنید.
</p>


## Todo

- [x] Arabic letters <span style="color: #d3d3d3;">ي ك</span>
- [x] Arabic numbers <span style="color: #d3d3d3;">٤ ٥ ٦</span>
- [x] English numbers <span style="color: #d3d3d3;">1 2 3 4 5 6 7 8 9 0</span>
- [x] English punctuations <span style="color: #d3d3d3;">? , " "</span>
- [x] Remove space before punctuations
- [x] Remove space between words
- [ ] Fix spacing of words ending with <span style="color: #d3d3d3;">شناسی</span> like <span style="color: #d3d3d3;">روان‌شناسی</span>
- [ ] Fix spacing of words starting with <span style="color: #d3d3d3;">سر</span> like <span style="color: #d3d3d3;">سرپرست</span>
- [ ] Fix zero-width non-joiner for words ending with <span style="color: #d3d3d3;">ای</span> <span style="color: #d3d3d3;">ها</span> <span style="color: #d3d3d3;">می</span> <span style="color: #d3d3d3;">های</span> <span style="color: #d3d3d3;">تر</span> etc.

## Build Setup

``` bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```
