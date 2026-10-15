# Git Branching Cheat Sheet

Git Branching Cheat Sheet ဆိုတာ Git မှာ branch တွေကို သုံးတဲ့အခါ လိုအပ်တဲ့ command တွေနဲ့ အသုံးပြုပုံတွေစုထားတဲ့ guide သဘောမျိုးပါ။ Project တစ်ခုကို developer အများကြီးအတူတူလုပ်တဲ့အခါ main branch ကို တိုက်ရိုက်ကြီးပြင်တာထက် ကိုယ်လုပ်မယ့် feature or bug fix အတွက် branch အသစ်တစ်ခုခွဲပြီး အလုပ်လုပ်တာက ပိုကောင်းပါတယ်။ အဲ့လိုလုပ်ထားရင် ကိုယ်ရေးနေတဲ့ code ကြောင့် main project ကို တိုက်ရိုက်မထိခိုက်ဘဲ လွတ်လွတ်လပ်လပ် develop and test လုပ်နိုင်ပါတယ်။

## Creating and Switching Branches

Branch တွေကိုကြည့်ချင်ရင် `git branch` ကိုသုံးပြီး branch အသစ်တစ်ခုလုပ်ပြီး အဲဒီ branch ကိုတစ်ခါတည်းပြောင်းချင်ရင် `git switch -c feature-name` (old command : git checkout -b feature-name) ကို သုံးပါတယ်။ ရှိပြီးသား branch တစ်ခုကို ပြောင်းချင်ရင် `git switch branch-name` (old command : git checkout branch-name) ကိုသုံးနိုင်ပါတယ်။ အရင် Git commands တွေမှာတော့ `git checkout` ကို branch ပြောင်းဖို့ သုံးကြပြီး နောက်ပိုင်းမှာ branch ပြောင်းတာအတွက် modern command `git switch` ကိုသုံးတာက english စာသဘောအရနားလည်ရလွယ်ပါတယ်။

## Merging and Deleting Branches

Branch တစ်ခုမှာ အလုပ်လုပ်ပြီးသွားတဲ့အခါ အဲဒီ့ branch ကို main branch ထဲ merge လုပ်ကြပါတယ်။ Merge ပြီးလို့ branch ကို မလိုတော့ဘူးဆိုရင် `git branch -d branch-name` နဲ့ ဖျက်နိုင်ပါတယ်။ Merge မလုပ်ရသေးတဲ့ branch ကိုဖျက်ချင်ရင်တော့ `git branch -D branch-name` ကို သုံးလို့ရပေမယ့် commit တွေဆုံးရှုံးနိုင်တာကြောင့် သတိထားရပါမယ်။

## Branch Naming

Team project တွေမှာ branch name ကိုလည်း အဓိပ္ပာယ်ရှိရှိပေးတာက အရေးကြီးပါတယ်။ ဥပမာ feature အသစ်လုပ်ရင် `feature/login`, bug ပြင်ရင် `fix/login-error`, အရေးတကြီးပြင်တာမျိုးဆို `hotfix/payment-error` အဲ့လိုမျိုး နာမည်ပေးတာပိုကောင်းပါတယ်။ ဒီလို naming တွေကိုစနစ်တျထားရင် branch list ကိုကြည့်လိုက်တာနဲ့ ဘယ် branch က ဘာအတွက်လဲဆိုတာ သိနိုင်ပါတယ်။

## Remote Branches

Remote repository မှာရှိတဲ့ branch တွေပါ ကြည့်ချင်ရင် `git branch -a` ကိုသုံးပါတယ်။ တခြား developer ဖန်တီးထားတဲ့ remote branch ကို local မှာဆက်လုပ်ချင်ရင် remote က update တွေကို `git fetch` နဲ့ယူပြီး အဲဒီ့ branch ကို switch လုပ်နိုင်ပါတယ်။

## Branching Workflow

Git Branching က project development ကို ပိုပြီးစနစ်ကျအောင် ကူညီပေးတဲ့ အရေးကြီးတဲ့ Git feature တစ်ခုပါ။ Feature တစ်ခုချင်းစီ၊ bug fix တစ်ခုချင်းစီကို branch သီးသန့်ခွဲပြီး အလုပ်လုပ်တဲ့အကျင့်ရှိရင် code conflict တွေကို လျှော့ချနိုင်သလို main branch ကိုလည်း ပိုတည်ငြိမ်အောင် ထိန်းထားနိုင်ပါတယ်။ အထူးသဖြင့် developer အများကြီးပူးပေါင်းလုပ်တဲ့ project တွေမှာ branching workflow ကို နားလည်ထားတာက အရေးကြီးပါတယ်။
