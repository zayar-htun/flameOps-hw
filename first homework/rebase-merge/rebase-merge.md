# Rebase vs Merge

Git မှာ branch နှစ်ခုကို ပေါင်းတဲ့အခါ သုံးတဲ့နည်းလမ်းတွေက `merge` နဲ့ `rebase` ဖြစ်ပါတယ်။ နှစ်ခုလုံးရဲ့ လုပ်တဲ့ပူံစံက branch တစ်ခုမှာရှိတဲ့ changes တွေကို တခြား branch နဲ့ ပေါင်းစည်းတာတူပေမဲ့ history ကို ကိုင်တွယ်ပုံမှာ ကွာခြားသွားပါတယ်။
 

## Example Scenario

ဥပမာ `main` branch မှာ `A` ဆိုတဲ့ commit ရှိတယ်ဆိုပြီးယူပါမယ်။

```text
A   ← main
```

ပြီးတော့ `A` ကနေ `feature` branch အသစ်ခွဲပြီး `B` နဲ့ `C` ဆိုတဲ့ commit နှစ်ခုကို feature branch မှာ လုပ်လိုက်ရင် history က ဒီလိုဖြစ်နေပါမယ်။

```text
A   ← main
 \
  B --- C   ← feature
```

feature branch ကို main ထဲ merge မလုပ်ခင် main branch မှာ တခြား developer တစ်ယောက်က `D` ဆိုတဲ့ commit အသစ်တစ်ခု တင်လိုက်တယ်ဆိုရင် history က ဒီလိုဖြစ်လာပါမယ်။

```text
A --- D   ← main
 \
  B --- C   ← feature
```

ဒီလိုနေရာမျိုူးမှာ `merge` နဲ့ `rebase` လုပ်ပုံက အတော်လေးကွာပါတယ်။

## Git Merge

`git merge` ကို သုံးရင် branch နှစ်ခုရဲ့ original history ကို မပြောင်းဘဲ ပြန်ပေါင်းတာမျိုးပါ။ အပေါ်က scenario မှာ feature branch ကို main ထဲ merge လုပ်ချင်ရင် အရင် main branch ကိုပြောင်းပြီး feature branch ကို merge လုပ်နိုင်ပါတယ်။

```bash
git switch main
git merge feature
```

Merge ပြီးရင် history ရဲ့ဖြစ်ပုံက ဒီလိုပါ

```text
A --- D ------- M   ← main
 \             /
  B --- C ----
```

ဒီမှာ `M` က merge commit ပါ `D` က main branch မှာ နောက်မှတင်လိုက်တဲ့ commit ဖြစ်ပြီး `B`, `C` က feature branch မှာရှိတဲ့ commits တွေဖြစ်ပါတယ်။

Merge က `B`, `C`, `D` commits တွေရဲ့ original history ကို မပြောင်းပါဘူး။ Branch နှစ်ခု ဘယ်နေရာမှာခွဲခဲ့တယ်၊ ဘယ်နေရာမှာ ပြန်ပေါင်းခဲ့တယ်ဆိုတာကို history ထဲမှာ သေချာရှင်းရှင်းလင်းလင်းမြင်နိုင်ပါတယ်။

team project တွေမှာ ဘယ် feature branch က ဘယ်အချိန် main ထဲဝင်လာခဲ့တယ်ဆိုတာ record ထားချင်ရင် merge က အဆင်ပြေပါတယ်။ Shared branch တွေမှာ history rewrite မလုပ်တာကြောင့် merge က ပိုလုံခြုံတဲ့နည်းလမ်းတစ်ခုလည်း ဖြစ်ပါတယ်။

## Git Rebase

`git rebase` ကတော့ feature branch မှာရှိတဲ့ commits တွေကို latest main commit ရဲ့နောက်မှာ ပြန်တင်ပေးတာဖြစ်ပါတယ်။

အပေါ်က scenario ကို ပြန်ကြည့်ရင် rebase မလုပ်ခင် history က ဒီလိုရှိပါတယ်။

```text
A --- D   ← main
 \
  B --- C   ← feature
```

Feature branch ထဲမှာ ဒီ command ကို run လုပ်နိုင်ပါတယ်။

```bash
git switch feature
git rebase main
```

Rebase ပြီးရင် history က ဒီလိုဖြစ်သွားပါတယ်။

```text
A --- D --- B' --- C'   ← feature
```

`B` နဲ့ `C` commits ရဲ့ changes တွေကို latest main commit `D` နောက်မှာ Git က ပြန်တည်ဆောက်ထားတဲ့ commits အသစ်လိုမျိုးဖြစ်ပါတယ်။

Code changes က တူပေမယ့် commit hash id တွေက original `B`, `C` နဲ့ မတူတော့ပါဘူး။ အဲ့ဒါကြောင့်မို့လို့ rebase ကို history rewrite လုပ်တဲ့ operation လို့ မြင်နိုင်ပါတယ်။
 

```bash
git switch main
git merge feature
```

နောက်ဆုံး history က ဒီလို ရိုးရှင်းသွားပါမယ်။

```text
A --- D --- B' --- C'   ← main
```

Merge commit သီးသန့်မလိုတော့ဘဲ history တစ်ကြောင်းတည်းလို မြင်ရပါတယ်။

## Merge နဲ့ Rebase ကွာခြားချက်

Merge မလုပ်ခင် history:

```text
A --- D
 \
  B --- C
```

Merge ပြီးရင်:

```text
A --- D ------- M
 \             /
  B --- C ----
```

Rebase ပြီးရင်:

```text
A --- D --- B' --- C'
```

ဒီနှစ်ခုကိုကြည့်ရင် ကွာခြားချက်ကို လွယ်လွယ်လေးမြင်နိုင်ပါတယ်။

`merge` က `D` ရှိတဲ့ main branch နဲ့ `B-C` ရှိတဲ့ feature branch ကို original history အတိုင်း ပြန်ပေါင်းတာဖြစ်ပြီး `rebase` ကတော့ `B-C` commits တွေကို latest main commit `D` ရဲ့နောက်မှာ ပြန်စီပေးတာဖြစ်ပါတယ်။

Merge ရဲ့ အားသာချက်က history ကို rewrite မလုပ်တာကြောင့် shared branch တွေမှာ ပိုလုံခြုံပါတယ်။ ဘယ် branch က ဘယ်အချိန်မှာ ခွဲပြီး ဘယ်အချိန်မှာ ပြန်ပေါင်းခဲ့လဲဆိုတာ history ထဲမှာ ထင်ရှားနေပါတယ်။

Rebase ရဲ့ အားသာချက်က history ကို linear ဖြစ်အောင်ထားနိုင်တာပါ။ Merge commit အများကြီး မရှိတော့တဲ့အတွက် `git log` ကို ပြန်ကြည့်တဲ့အခါ ပိုပြီးဖတ်ရလွယ်ပါတယ်။

ဒါပေမယ့် rebase က ကိုယ့် local feature branch မှာ latest main changes ကိုယူပြီး history ကို ရှင်းချင်တဲ့အခါ သုံးတာပိုသင့်တော်ပါတယ်။

## Conflict Handling

Conflict ဖြစ်တဲ့အခါ merge နဲ့ rebase နှစ်ခုလုံးမှာ manual ဖြေရှင်းလို့၇ပါတယ်။ Merge conflict ဖြစ်ရင် conflict ကိုဖြေရှင်းပြီး commit ပြန်လုပ်နိုင်ပါတယ်။ Rebase conflict ဖြစ်ရင် conflict ကိုဖြေရှင်းပြီးနောက်


 
```bash
git rebase --abort
```

နဲ့ rebase မလုပ်ခင် အခြေအနေကိုလဲ ပြန်သွားလို့ရနိုင်ပါတယ်။

## Summary

 `merge` ကို branch နှစ်ခုကို **history အတိုင်းပေါင်းတာ** ၊ `rebase` ကို feature commits တွေကို **latest main ရဲ့နောက်မှာ ပြန်စီတာ** လို့ မှတ်ထားလို့ရနိုင်ပါတယ်။ Team shared branch တွေအတွက် merge က ပိုလုံခြုံပြီး ကိုယ့် local feature branch history ကို သန့်သန့်ရှင်းရှင်းထားချင်တဲ့အခါ rebase ကို အသုံးပြုတာ ပိုကောင်းပါတယ်။