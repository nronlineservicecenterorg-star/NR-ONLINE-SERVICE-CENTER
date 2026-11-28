NR ONLINE SERVICE CENTER — ওয়েবসাইট প্যাকেজ

ফাইল:
- index.html: আপনার দেওয়া ওয়েবসাইট, সঙ্গে প্রাথমিক SEO metadata
- robots.txt: সার্চ ইঞ্জিন crawler-কে সাইট crawl করতে অনুমতি দেয়

ফ্রি হোস্টিং:
1. GitHub-এ একটি account খুলুন।
2. একটি নতুন Public repository তৈরি করুন।
3. index.html এবং robots.txt আপলোড করুন।
4. Repository Settings > Pages-এ যান।
5. Deploy from a branch নির্বাচন করে main এবং /(root) সিলেক্ট করে Save করুন।
6. GitHub যে website URL দেবে সেটি দিয়ে সাইট খুলে পরীক্ষা করুন।

Google Search:
1. Google Search Console-এ গিয়ে URL-prefix property হিসেবে আপনার প্রকাশিত ওয়েবসাইট URL যোগ করুন।
2. প্রদত্ত পদ্ধতিতে ownership verify করুন।
3. সাইট প্রকাশিত হওয়ার পর sitemap.xml যোগ করা যায়। নিজের live domain/URL জানা না থাকায় এই প্যাকেজে ভুল sitemap URL তৈরি করা হয়নি।
4. URL Inspection থেকে homepage-এ Request Indexing দিন। Google-এ দেখাতে সময় লাগতে পারে; indexing নিশ্চিত নয়।

গুরুত্বপূর্ণ সীমাবদ্ধতা:
- এই HTML-এ login/registration browser localStorage-এ চলে; এটি প্রকৃত server-side account system নয়।
- পাসওয়ার্ড browser-এ plain text হিসেবে রাখা হয়। বাস্তব গ্রাহকের password বা সংবেদনশীল তথ্য সংগ্রহের জন্য এটি নিরাপদ নয়।
- আলাদা server/database ছাড়া customer registration, login, feedback form অন্য device-এ sync হবে না।
- Tailwind, PDF ও অন্যান্য library এবং Google Fonts-এর কিছু অংশ CDN থেকে লোড হয়; সম্পূর্ণ কাজের জন্য internet connection প্রয়োজন।
- আপনার HTML-এ 4652.png নামে একটি local logo reference ছিল; অনুপস্থিত logo-র জন্য inline NR fallback যোগ করা হয়েছে।
- Google Search-এ আসা বিনামূল্যে, তবে ranking বা নির্দিষ্ট সময়ে indexing-এর নিশ্চয়তা নেই।
