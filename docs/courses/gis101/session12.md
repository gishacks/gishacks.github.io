---
title: جلسه 14 - ساخت نقشه آنلاین
---
این جلسه راجع به spatial join است. جلسه ی 13 را با می کنیم و لایه ی بیمارستان را وارد می کنیم.![1](https://github.com/user-attachments/assets/67f6761b-722e-483d-960c-013e7eb263b7)
 ما می خواهیم اطلاعات بیمارستان را وارد محلات کنیم. روی لایه ی محلات راست کلیک می کنیم و گزینه ی join and relate را می زنیم و بعد گزینه ی add spatial join را می زنیم. در قسمت target محلات را می زنیم و در قسمت join گزینه ی بیمارستان را می زنیم و اوکی را می زنیم![2](https://github.com/user-attachments/assets/315343e6-7133-4d1c-83ce-e5c3ec196207)
.
در جدول محلات یک فیلد جدید می سازیم به نام بیمارستان و یک دانه دیگه به نام جمعیت.![3](https://github.com/user-attachments/assets/e70be479-c66b-4982-b47a-b6b226d4bae0)
 حال این دو فیلد را سیو می کنیم و راست کلیک می کنیم و caluculate field را انتخاب می کنیم(در قسمت فیلدز گزینه ی join count را انتخاب می کنیم) ![4](https://github.com/user-attachments/assets/2e5a20bb-a751-4e3b-8f97-c8848cfd37c0![5](https://github.com/user-attachments/assets/a5ab47d9-f6c8-4443-b48a-cb7d091e4202)
)
سپس در لایه ی محلات remove all joins را می زنیم![6](https://github.com/user-attachments/assets/d7b36be3-fb85-4f3a-ab7a-bac8cdc2ba0c)
 و دوباره لایه ی jamiat block را وارد سیستم می کنیم![7](https://github.com/user-attachments/assets/981a5ebd-9008-4cab-80cb-99f6c4b25399)
 و دوباره راست کلیک کرده و spatial join را انتخاب می کنیم. و در قسمت جویت جمعیت بلوک را انتخاب می کنیم پایین تر در بخش قیلدز تمام فیلد های حال حاضر را ریموو می کنیم![8](https://github.com/user-attachments/assets/f38ea074-acc4-4564-a5ac-4dcaa0cb8e9a)
 و سپس در قسمت add fields گزینه ی jamiat را انتخاب کرده و sum را می زنیم و سپس ok را می زنیم.![9](https://github.com/user-attachments/assets/1b52a077-919d-46d4-adfc-deaffe3f6263)
 (می خواهیم ببینیم بحرانی ترین محله کجاست؟) دوباره روی ستون population راست کلیک می کنیم و گزینه ی calculate را انتخاب می کنیم و jamiat sum را انتخاب کرد![10](https://github.com/user-attachments/assets/876d36fa-6673-489b-a6fd-0b84a140eb68)
ه و اوکی را می زنیم. در اخر برای هر سه لایه ی وارد شده در بخش symbology graduated colors را می زنیم تا نقشه ها تهیه شود![11](https://github.com/user-attachments/assets/3d1a6344-b9a1-480b-80ef-063ecec31e89![12](https://github.com/user-attachments/assets/5d9b08cd-2ec9-4b37-a378-0267fc577d6c)
)
.
