# Merge Strategies

## ၁. different types of merge strategies

merge တယ်ဆိုတာ branch နှစ်ခုက changes တွေကိုပေါင်းတာဖြစ်ပါတယ်

### အသုံးများတဲ့ merge strategies တွေက :
- Fast-forward merge
- No-fast-forward
- Squash merge တို့ပဲဖြစ်ပါတယ်

### Fast-forward merge
Fast-forward ဆိုတာ main branch မှာ အခြား commit အသစ်တွေမရှိဘဲ feature branch ကပဲ အသစ် update တွေရှိတဲ့အခါ အသုံးပြုနိုင်တဲ့ merge ပုံစံဖြစ်ပါတယ်။ Merge လုပ်လိုက်တဲ့အခါ merge commit ကိုအသစ် create မလုပ်ဘဲ main branch pointer ကို feature branch ရဲ့နောက်ဆုံး commit ဆီ ရွှေ့ပေးတာပါ။ ဒီ strategy မှာကတော့ Git history က ရိုးရှင်းပြီး တစ်လိုင်းထဲရှိတော့ ဖတ်ရလွယ်ပါတယ်။ များသောအားဖြင့် history ကို သန့်သန့်ရှင်းရှင်းထားချင်တဲ့အခါ၊ pj သေးတဲ့အခါ ဒီနည်းလမ်းက အသုံးဝင်ပါတယ်။

### No-fast-forward
No-fast-forward  မှာကတော့ fast-forward လုပ်လို့ရနေတဲ့အခြေအနေမှာတောင် merge commit တစ်ခုကို သီးသန့်ဖန်တီးပေးတဲ့ပုံစံမျိုးဖြစ်ပါတယ်။ ဒီလိုလုပ်ထားတဲ့အတွက် feature branch တစ်ခုကို ဘယ်အချိန်မှာ main branch ထဲ merge လုပ်ခဲ့လဲဆိုတာ history ထဲမှာ ရှင်းရှင်းလင်းလင်းမြင်ရပါတယ်။ Team project တွေမှာ feature တစ်ခုချင်းစီရဲ့ development history ကို သိမ်းထားချင်တဲ့အခါ ဒီနည်းလမ်း ပိုအသုံးဝင်ပါတယ်။ ဒါပေမယ့် merge commit တွေများလာရင် history က အနည်းငယ်ရှုပ်လာနိုင်ပါတယ်။

### Squash merge
Squash merge ဆိုတာ feature branch ထဲမှာရှိတဲ့ commit အများကြီးကို commit တစ်ခုတည်းအဖြစ် စုလိုက်ပြီး main branch ထဲ merge လုပ်တဲ့နည်းလမ်းဖြစ်ပါတယ်။ Development လုပ်နေစဉ်မှာ fix တို့ update တို့ small change တို့လို commit သေးသေးလေးတွေ အများကြီးရှိနေတတ်တဲ့အတွက် squash လုပ်လိုက်ရင် main branch history က ပိုသန့်သွားပါတယ်။ Feature တစ်ခုလုံးကို commit တစ်ခုအဖြစ်ပဲ history ထဲမှာ မြင်ရတာကြောင့် နောက်ပိုင်း ပြန်ကြည့်တဲ့အခါလည်း နားလည်ရလွယ်ပါတယ်။ ဒါပေမဲ့ feature branch ရဲ့ commit အသေးစိတ် history ကို ပြန်လိုချင်တဲ့အချိန် ပြန်ကြည့်ချင်တဲ့အချိန်မှာ main branch ထဲမှာ အသေးစိတ်မမြင်ရတော့ပါဘူး။