# Git Time Travel

Git Time Travel ဆိုတာ Git history ထဲမှာရှိတဲ့ အရင် commit တွေကို ပြန်ကြည့်တာ၊ အရင်အခြေအနေကို ပြန်သွားတာ၊ မှားသွားတဲ့ changes တွေကို ပြန်ပြင်တာမျိုးဖြစ်ပါတယ်။ Git မှာ time travel လုပ်လို့ရတဲ့ command တွေက git log, git checkout, git restore, git reset, git revert, git rebase နဲ့ git blame စတဲ့ command တွေပါ။ အဲ့ commands တွေကို အသုံးပြုပြီး project history ကို ပြန်စစ်ဆေး၊ ပြန်ပြင်ဆင်နိုင်ပါတယ်။

## Viewing History — git log

Project ထဲမှာ ဘယ် commit တွေရှိလဲ၊ ဘယ်အချိန်မှာ ဘာတွေပြင်ခဲ့လဲ သိချင်ရင် git log ကို သုံးပြုနိုင်ပါတယ်။ History ကို တိုတိုရှင်းရှင်းကြည့်ချင်ရင် git log --oneline ကိုသုံးနိုင်ပြီး branch အားလုံးနဲ့ commit ဆက်ဆက်တာကိုူ ကြည့်ချင်ရင် git log --oneline --graph --decorate --all ကို သုံးလို့ရပါတယ်။ အရင် commit တစ်ခုခုကို ပြန်ကြည့်ချင်တဲ့အခါ လိုအပ်တဲ့ commit hash id ကို ဒီ history ကနေ ရယူနိုင်ပါတယ်။

## Inspecting Past Commits — git checkout

အရင် commit တစ်ခုမှာ ဘယ်လိုရှိခဲ့လဲဆိုတာ ကြည့်ချင်ရုံပဲဆိုရင် git checkout <commit-hash> ကို အသုံးပြုနိုင်ပါတယ်။ ဒီလိုလုပ်လိုက်ရင် detached HEAD အခြေအနေကို ရောက်သွားနိုင်ပါတယ်။ အဲဒီအခြေအနေမှာ code ကို စစ်ကြည့်နိုင်ပေမယ့် ပုံမှန် branch workflow အနေနဲ့ အလုပ်လုပ်တာမဟုတ်ပါဘူး။ စစ်ပြီးသွားရင် git switch main လို command နဲ့ လက်ရှိ branch ကိုပြန်သွားနိုင်ပါတယ်။

## Restoring Files — git restore

File တစ်ခုကို ပြင်မိပြီး commit မလုပ်ရသေးဘူးဆိုရင် git restore <file> ကို သုံးပြီး နောက်ဆုံး commit အခြေအနေကို ပြန်ယူနိုင်ပါတယ်။ ဒီ command ကို သုံးလိုက်ရင် commit မလုပ်ထားတဲ့ changes တွေ အကုန်ပျောက်သွားနိုင်တာကြောင့် အသုံးမပြုခင် ကိုယ်ရေးထားတဲ့ code လိုသေးလားဆိုတာ စစ်သင့်ပါတယ်။ ui ကနေလဲ back icon လို မျိုးနှပ်ပြီးသုံးလို့ရပါတယ်။

## Resetting History — git reset

git reset ဆိုတာ commit history ကို အရင် commit တစ်ခုဆီ ပြန်ရွှေ့ဖို့ သုံတဲ့ command ဖြစ်ပါတယ်။ အဓိကအားဖြင့် local မှာ commit မှားလုပ်မိတာဖြစ်ဖြစ် commit ပြန်စီချင်တဖြစ်ဖြစ် staging area ကို ပြန်ဖြုတ်ချင်တာမျိုးမှာဖ့စ်ဖြစ် အသုံးများပါတယ်။ git reset မှာ --soft, --mixed, --hard ဆိုပြီး အဓိက mode သုံးမျိုးရှိပါတယ်။

### Soft Reset

git reset --soft <commit> ကို သုံးရင် commit history ကို အရင်နေရာဆီ ပြန်ရွှေ့ပေးပး ကိုယ်ပြင်ထားတဲ့ changes တွေကို staging area ထဲမှာ ဆက်ထားပေးပါတယ်။ ဥပမာ commit message မှားတာ၊ commit နှစ်ခုကို ပြန်စုပြီး commit တစ်ခုတည်း ပြန်လုပ်ချင်တာမျိုးမှာ အသုံးဝင်ပါတယ်။ Code ကို မဖျက်ဘဲ commit ကိုပဲ ပြန်ဖြုတ်ချင်ရင် --soft ကို သုံးနိုင်ပါတယ်။

### Mixed Reset

git reset --mixed <commit> က default mode ဖြစ်ပါတယ်။ git reset <commit> လို့ပဲ ရေးလည်း mixed mode အနေနဲ့ အလုပ်လုပ်ပါတယ်။ ဒီ mode က commit ကို ပြန်ရွှေ့ပေးသလို staging area ထဲက file တွေကို unstage လုပ်ပေးပါတယ်။ ဒါပေမယ့် code changes တွေက working directory ထဲမှာ ဆက်ရှိနေမှာပါ။ Commit နဲ့ staging ကို ပြန်ရှင်းပြီး file တွေကို ပြန်စစ်ပြီးမှ add နဲ့ commit ပြန်လုပ်ချင်တဲ့အခါ အသုံးဝင်ပါတယ်။

### Hard Reset

git reset --hard <commit> ကတော့ commit history, staging area နဲ့ working directory ကိုပါ အရင် commit အခြေအနေပြန်ဖြစ်အောင် လုပ်ပေးပါတယ်။ မလိုချင်တဲ့ local changes တွေကို အကုန်ဖယ်ပြီး အရင် version ကို တိတိကျကျ ပြန်သွားချင်တဲ့အခါ အသုံးပြုနိုင်ပါတယ်။ ဒါပေမယ့် commit မလုပ်ထားတဲ့ code တွေ ပျောက်သွားနိုင်တာကြောင့် --hard ကို အထူးသတိထားပြီး သုံးသင့်ပါတယ်။

### Reset Modes 

အလွယ်မှတ်မယ်ဆိုရင် --soft က commit ကိုပဲ ပြန်ဖြုတ်ပြီး changes ကို staged အနေအထားမှာထားတယ်၊ --mixed က commit နဲ့ staging ကို ပြန်ဖြုတ်ပြီး changes ကို working directory ထဲမှာထားတယ်။ --hard ကတော့ commit, staging နဲ့ working changes တွေကိုပါ ဖယ်ရှားနိုင်ပါတယ်။

## Undoing Commits — git revert

git revert ဆိုတာ အရင် commit တစ်ခုရဲ့ changes ကို ပြန်ဖျက်ပေးပြှီး commit အသစ်တစ်ခု ဖန်တီးပေးတာဖြစ်ပါတယ်။ git reset လို history ကို ပြန်ရေးတာမဟုတ်ဘဲ အရင် commit ကို history ထဲမှာ ဆက်ထားပြီး အဲဒီ commit ရဲ့  changes တွေကို ပြန်ဖယ်ပြီး commit အသစ်တစ်ခု ထပ်ထည့်တာဖြစ်ပါတယ်။ ဒါကြောင့် remote repository မှာ push လုပ်ပြီးသား commit သို့မဟုတ် team အားလုံးအသုံးပြုနေတဲ့ shared branch တွေအတွက် git revert က ပိုလုံခြုံပါတယ်။

ဥပမာ production မှာ bug ဖြစ်စေတဲ့ commit တစ်ခုကို push လုပ်ပြီးသားဆိုရင် git revert <commit-hash> ကို သုံးပြီး အဲဒီ commit ရဲ့ changes တွေကို ပြန်ဖယ်နိုင်ပါတယ်။ ဒီနည်းမှာ history မပျောက်တာကြောင့် ဘာ commit ကို ဘယ်အချိန်မှာ ပြန်ပြင်ခဲ့လဲဆိုတာလည်း နောက်ပိုင်း ပြန်ကြည့်နိုင်ပါတယ်။

## Reordering History — git rebase

git rebase ဆိုတာ branch တစ်ခုမှာရှိတဲ့ commit တွေကို တခြား branch ရဲ့ နောက်ဆုံး commit ပေါ်မှာ ပြန်စီပေးတဲ့ command ဖြစ်ပါတယ်။ ဥပမာ main ကနေ feature-login branch ကို create ပြီးတော့ main branch မှာ commit အသစ်တွေ ထပ်ဝင်လာတယ့်အခါမျိုးဆိုရင် Feature branch ကနေ git rebase main လုပ်ရင် ကိုယ့် feature commits တွေကို latest main ရဲ့ နောက်မှာ ပြန်တင်ပေးပါတယ်။

Rebase ရဲ့ အားသာချက်က commit history ကို သန့်သန့်ရှင်းရှင်းနဲ့ linear ဖြစ်အောင်ထားနိုင်တာပါ။ Merge commit အများကြီးမထွက်ဘဲ history ကို ဖတ်ရလွယ်ပါတယ်။ ဒါပေမယ့် rebase က commit history ကို rewrite လုပ်တာဖြစ်တဲ့အတွက် တခြား developer တွေ သုံးနေတဲ့ shared branch ပေါ်မှာ မလိုအပ်ဘဲ rebase မလုပ်သင့်ပါဘူး။ Local feature branch မှာ သုံးတာက ပိုသင့်တော်ပါတယ်။

## Recovering Commits — git reflog

တစ်ခါတစ်လေ git reset --hard လုပ်မိတာ၊ branch တစ်ခုကို မှားဖျက်မိတာကြောင့် commit ပျောက်သွားတာမျိုး ဖြစ်နိုင်ပါတယ်။ အဲ့ကျရင် git reflog ကို အသုံးပြုပြီး HEAD ရွေ့ခဲ့တဲ့ history ကို ပြန်ကြည့်နိုင်ပါတယ်။ Reflog ထဲမှာ ပျောက်သွားတဲ့ commit hash ကို တွေ့ရင် အဲဒီ commit ဆီပြန်သွားတာ၊ branch အသစ်ပြန်ဖန်တီးတာမျိုး လုပ်နိုင်ပါတယ်။  

## Tracking Line History — git blame

`git blame <file>` ဆိုတာ file တစ်ခုထဲက code line တစ်ကြောင်းချင်းစီကို ဘယ် developer က ဘယ် commit မှာ နောက်ဆုံးပြင်ခဲ့လဲဆိုတာ ကြည့်ဖို့ သုံးတဲ့ command ဖြစ်ပါတယ်။ Bug တစ်ခုစဖြစ်လာတဲ့နေရာကို ရှာချင်တာမျိုး line တစ်ကြောင်းရဲ့ history ကို ပြန်ကြည့်ချင်တာမျိုးမှာ အသုံးဝင်ပါတယ်။

## Command Summary

command တစ်ခုချင်းစီရဲ့ ရည်ရွယ်ချက်ကို ခွဲသိထားဖို့ အရေးကြီးပါတယ်။ History ကိုကြည့်ဖို့ git log, အရင် commit ကို စစ်ကြည့်ဖို့ git checkout, file changes ပြန်ယူဖို့ git restore, local history ကို ပြန်ရွှေ့ဖို့ git reset, push လုပ်ပြီးသား commit ကို safe ဖြစ်ဖြစ် ပြန်ပြင်ဖို့ git revert, branch history ကို ပြန်စီဖို့ git rebase နဲ့ ပျောက်သွားတဲ့ commit တွေကို ရှာဖို့ git reflog ကို အသုံးပြုနိုင်ပါတယ်။
 
## Conclusion

Git Time Travel ကို နားလည်ထားရင် code မှားပြင်မိတာဖြစ်ဖြစ် commit မှားလုပ်မိတာဖြစ်ဖြစ် အရင် version ကို ပြန်စစ်ချင်တာ ဒါမှမဟုတ် history ကို ပြန်စီချင်တာမျိုးတွေမှာ အကူအညီဖြစ်ပါတယ်။ အရေးကြီးတာက reset, rebase လို history ကို ပြောင်းလဲနိုင်တဲ့ command တွေကို shared branch မှာ သတိထားပြီး အသုံးပြုဖို့နဲ့ push လုပ်ပြီးသား history ကို ပြင်တဲ့အခါ revert လိုနည်းလမ်းကို သုံးဖို့ဖြစ်ပါတယ်။