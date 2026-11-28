<img width="678" height="452" alt="7884" src="https://github.com/user-attachments/assets/47ec744d-40a3-46e6-a42a-482ce065d7b6" />
<img width="615" height="1010" alt="7876" src="https://github.com/user-attachments/assets/b7ce8fda-4406-4c4b-aadb-73e3b27cbc2f" />


HTML icon
cash-memo-maker
<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>ক্যাশ মেমো মেকার (Cash Memo Maker) - NR Online Service Center</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Hind+Siliguri:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --cm-bg-page: #05180d;
            --cm-bg-card: #092415;
            --cm-bg-input: #071c10;
            --cm-border-card: #164b2c;
            --cm-border-input: #1c5a36;
            --memo-accent: #0f7644;
            --memo-tint: #eef7f2;
            --memo-border: #86c5a3;
        }
        body {
            font-family: 'Hind Siliguri', sans-serif;
            background-color: var(--cm-bg-page);
            color: #e2f5ea;
            margin: 0;
            padding: 0;
        }
        .cm-card {
            background-color: var(--cm-bg-card);
            border: 1px solid var(--cm-border-card);
            border-radius: 12px;
            padding: 14px;
        }
        .cm-input {
            background-color: var(--cm-bg-input);
            border: 1px solid var(--cm-border-input);
            color: #f0fdf4;
            border-radius: 6px;
            padding: 7px 10px;
            font-size: 13px;
            width: 100%;
        }
        .cm-input::placeholder {
            color: #6b8f7a;
        }
        .cm-input:focus {
            outline: none;
            border-color: #22c55e;
            box-shadow: 0 0 0 2px rgba(34, 197, 94, 0.2);
        }
        .cm-badge {
            width: 22px;
            height: 22px;
            border-radius: 9999px;
            background-color: #16a34a;
            color: #ffffff;
            font-size: 12px;
            font-weight: 700;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            flex-shrink: 0;
        }
        .cm-paper-pill,
        .cm-lang-pill {
            border: 1px solid #1e623b;
            background-color: #071c10;
            color: #d1fae5;
            border-radius: 8px;
            padding: 5px 12px;
            font-size: 12px;
            font-weight: 600;
            cursor: pointer;
        }
        .cm-paper-pill.active,
        .cm-lang-pill.active {
            background-color: #16a34a;
            border-color: #22c55e;
            color: #ffffff;
        }
        .cm-swatch {
            width: 26px;
            height: 26px;
            border-radius: 9999px;
            border: 2px solid #ffffff;
            cursor: pointer;
        }
        .cm-swatch.active {
            transform: scale(1.12);
            box-shadow: 0 0 0 3px rgba(34, 197, 94, 0.7);
        }
        .cm-paper {
            background-color: #ffffff;
            color: #111827;
            border-radius: 4px;
            padding: 12px;
            margin: 0 auto;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.45);
            transition: max-width 0.2s ease;
        }
        .cm-paper.size-a4 { max-width: 100%; }
        .cm-paper.size-a5 { max-width: 430px; }
        .cm-paper.size-80mm { max-width: 310px; padding: 8px; }
        .cm-frame {
            border: 2px solid var(--memo-accent);
            padding: 12px 14px 10px;
            background-color: #ffffff;
        }
        .cm-table {
            width: 100%;
            border-collapse: collapse;
            border: 1.5px solid var(--memo-accent);
            font-size: 12px;
        }
        .cm-table thead th {
            background-color: var(--memo-accent);
            color: #ffffff;
            font-weight: 700;
            padding: 5px 6px;
            border-right: 1px solid rgba(255, 255, 255, 0.35);
            text-align: left;
        }
        .cm-table thead th:last-child { border-right: none; }
        .cm-table tbody td {
            padding: 4px 6px;
            height: 23px;
            border-right: 1px solid var(--memo-border);
            color: #111827;
            font-size: 12px;
        }
        .cm-table tbody td:last-child { border-right: none; }
        .cm-table tbody tr:nth-child(even) { background-color: var(--memo-tint); }
        .cm-dotted {
            border-bottom: 1px dashed #9ca3af;
            display: inline-block;
            min-width: 70px;
            padding: 0 4px;
            color: #111827;
            font-weight: 500;
        }
        @media print {
            body * { visibility: hidden; }
            #cm-printable-area, #cm-printable-area * { visibility: visible; }
            #cm-printable-area {
                position: fixed;
                left: 0;
                top: 0;
                width: 100%;
                box-shadow: none !important;
            }
        }
    </style>
</head>
<body>
    <div class="max-w-7xl mx-auto p-4 sm:p-6 space-y-4">
        <div class="flex flex-wrap items-center justify-between gap-2 border-b border-[#164b2c] pb-3">
            <div>
                <h1 class="text-lg sm:text-2xl font-bold">
                    ক্যাশ <span class="text-[#facc15]">মেমো</span> মেকার <span class="text-emerald-300 text-sm sm:text-base">(Cash Memo Maker)</span>
                </h1>
                <p class="text-xs text-emerald-300/80">NR ONLINE SERVICE CENTER — বাংলা ও ইংরেজি ক্যাশ মেমো তৈরি, প্রিন্ট ও PDF ডাউনলোড</p>
            </div>
            <span class="bg-[#16a34a] text-white text-xs font-bold px-3 py-1 rounded-full">A4 / A5 / 80mm Ready</span>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-12 gap-4 items-start">
            <!-- Left Form Column -->
            <div class="lg:col-span-5 space-y-3.5">
                <!-- 1. দোকানের তথ্য -->
                <div class="cm-card space-y-2.5">
                    <div class="flex items-center gap-2">
                        <span class="cm-badge">1</span>
                        <h3 class="text-sm font-bold text-white">দোকানের তথ্য <span class="text-[#22c55e]">(Shop Details)</span></h3>
                    </div>
                    <div>
                        <label class="block text-xs text-[#d1fae5] mb-1">দোকানের নাম *</label>
                        <input id="cm-shopName" type="text" class="cm-input" placeholder="দোকানের নাম এখানে লিখুন" />
                    </div>
                    <div>
                        <label class="block text-xs text-[#d1fae5] mb-1">মালিকের নাম (প্রোঃ)</label>
                        <input id="cm-ownerName" type="text" class="cm-input" placeholder="মালিকের নাম লিখুন" />
                    </div>
                    <div>
                        <label class="block text-xs text-[#d1fae5] mb-1">ঠিকানা</label>
                        <input id="cm-shopAddress" type="text" class="cm-input" placeholder="দোকান, পৌরসভা, জেলা" />
                    </div>
                    <div class="grid grid-cols-2 gap-2">
                        <div>
                            <label class="block text-xs text-[#d1fae5] mb-1">মোবাইল *</label>
                            <input id="cm-shopMobile" type="text" class="cm-input" placeholder="987XX-XXXXX" />
                        </div>
                        <div>
                            <label class="block text-xs text-[#d1fae5] mb-1">GSTIN</label>
                            <input id="cm-shopGstin" type="text" class="cm-input" placeholder="(যদি থাকে লিখুন)" />
                        </div>
                    </div>
                    <div class="flex flex-wrap items-center justify-between gap-2 pt-1 text-xs">
                        <label class="inline-flex items-center gap-1.5 cursor-pointer">
                            <input id="cm-chkShowLogo" type="checkbox" checked />
                            <span>লোগো / ব্যাজ দেখান</span>
                        </label>
                        <label class="bg-[#0e351f] hover:bg-[#144a2b] border border-[#1e623b] text-[#86efac] px-2.5 py-1 rounded cursor-pointer">
                            🖼️ লোগো আপলোড
                            <input id="cm-logoUpload" type="file" accept="image/*" class="hidden" />
                        </label>
                    </div>
                    <label class="inline-flex items-center gap-1.5 text-xs cursor-pointer">
                        <input id="cm-chkEnableGst" type="checkbox" checked />
                        <span>ক্রেতার জন্য GST প্রদান করা হবে</span>
                    </label>
                </div>

                <!-- 2. গ্রাহক বা ক্রেতা -->
                <div class="cm-card space-y-2.5">
                    <div class="flex items-center gap-2">
                        <span class="cm-badge">2</span>
                        <h3 class="text-sm font-bold text-white">গ্রাহক বা ক্রেতা <span class="text-[#22c55e]">(Memo &amp; Customer)</span></h3>
                    </div>
                    <div class="grid grid-cols-2 gap-2">
                        <div>
                            <label class="block text-xs text-[#d1fae5] mb-1">বিলের নং</label>
                            <input id="cm-billNo" type="text" class="cm-input" value="1" />
                        </div>
                        <div>
                            <label class="block text-xs text-[#d1fae5] mb-1">তারিখ</label>
                            <input id="cm-billDate" type="date" class="cm-input" />
                        </div>
                    </div>
                    <div>
                        <label class="block text-xs text-[#d1fae5] mb-1">ক্রেতার নাম</label>
                        <input id="cm-custName" type="text" class="cm-input" placeholder="ক্রেতার নাম লিখুন" />
                    </div>
                    <div class="grid grid-cols-2 gap-2">
                        <div>
                            <label class="block text-xs text-[#d1fae5] mb-1">মোবাইল</label>
                            <input id="cm-custMobile" type="text" class="cm-input" placeholder="মোবাইল নম্বর" />
                        </div>
                        <div>
                            <label class="block text-xs text-[#d1fae5] mb-1">ঠিকানা</label>
                            <input id="cm-custAddress" type="text" class="cm-input" placeholder="ঠিকানা" />
                        </div>
                    </div>
                </div>

                <!-- 3. পণ্যের বিবরণ -->
                <div class="cm-card space-y-2.5">
                    <div class="flex items-center gap-2">
                        <span class="cm-badge">3</span>
                        <h3 class="text-sm font-bold text-white">পণ্যের বিবরণ <span class="text-[#22c55e]">(Items)</span></h3>
                    </div>
                    <div class="grid grid-cols-12 gap-1.5 text-[11px] font-semibold text-[#a7f3d0]">
                        <div class="col-span-6">বিবরণ / Item</div>
                        <div class="col-span-2 text-center">পরিমাণ</div>
                        <div class="col-span-3 text-center">দর ₹</div>
                        <div class="col-span-1"></div>
                    </div>
                    <div id="cm-itemsList" class="space-y-2"></div>
                    <button id="cm-btnAddItem" type="button" class="w-full bg-[#22c55e] hover:bg-[#16a34a] text-[#052e16] font-bold text-xs py-2 rounded-md cursor-pointer">
                        + আরও আইটেম যোগ করুন / Add Item
                    </button>
                </div>

                <!-- 4. হিসাব ও পেমেন্ট -->
                <div class="cm-card space-y-2.5">
                    <div class="flex items-center gap-2">
                        <span class="cm-badge">4</span>
                        <h3 class="text-sm font-bold text-white">হিসাব ও পেমেন্ট <span class="text-[#22c55e]">(Total &amp; Payment)</span></h3>
                    </div>
                    <div class="grid grid-cols-2 gap-2">
                        <div>
                            <label class="block text-xs text-[#d1fae5] mb-1">ছাড় % (Discount)</label>
                            <input id="cm-discountPct" type="number" min="0" max="100" step="any" class="cm-input" value="0" />
                        </div>
                        <div id="cm-gstFieldWrapper">
                            <label class="block text-xs text-[#d1fae5] mb-1">GST %</label>
                            <input id="cm-gstPct" type="number" min="0" max="100" step="any" class="cm-input" value="0" />
                        </div>
                    </div>
                    <div class="grid grid-cols-2 gap-2">
                        <div>
                            <label class="block text-xs text-[#d1fae5] mb-1">মোট দেয় (Paid)</label>
                            <input id="cm-paidAmount" type="number" min="0" step="any" class="cm-input" placeholder="(মোট টাকা)" />
                        </div>
                        <div>
                            <label class="block text-xs text-[#d1fae5] mb-1">পেমেন্ট মোড</label>
                            <select id="cm-paymentMode" class="cm-input">
                                <option value="নগদ / Cash">নগদ / Cash</option>
                                <option value="বিকাশ / bKash">বিকাশ / bKash</option>
                                <option value="নগদ (Nagad)">নগদ (Nagad)</option>
                                <option value="UPI / অনলাইন">UPI / অনলাইন</option>
                                <option value="ব্যাংক / Bank">ব্যাংক / Bank</option>
                                <option value="বাকি / Due">বাকি / Due</option>
                            </select>
                        </div>
                    </div>
                    <div>
                        <label class="block text-xs text-[#d1fae5] mb-1">নিয়মিত নোট</label>
                        <input id="cm-memoNote" type="text" class="cm-input" placeholder="ধন্যবাদ, আবার আসবেন" />
                    </div>
                    <div class="bg-[#071c10] border border-[#1c5a36] rounded-md px-3 py-2 flex items-center justify-between">
                        <span class="text-xs font-semibold text-[#d1fae5]">সর্বমোট / Total</span>
                        <span id="cm-formDueTotal" class="text-sm font-bold text-[#facc15]">₹0</span>
                    </div>
                </div>

                <!-- 5. কাগজ ও ডিজাইন -->
                <div class="cm-card space-y-3">
                    <div class="flex items-center gap-2">
                        <span class="cm-badge">5</span>
                        <h3 class="text-sm font-bold text-white">কাগজ ও ডিজাইন <span class="text-[#22c55e]">(Paper &amp; Design)</span></h3>
                    </div>
                    <div>
                        <span class="block text-xs text-[#d1fae5] mb-1.5">কাগজের সাইজ / Paper</span>
                        <div class="flex flex-wrap gap-2">
                            <button type="button" class="cm-paper-pill active" data-size="a4">A4</button>
                            <button type="button" class="cm-paper-pill" data-size="a5">A5 (ছোট A4)</button>
                            <button type="button" class="cm-paper-pill" data-size="80mm">রশিদ 80mm</button>
                        </div>
                    </div>
                    <div>
                        <span class="block text-xs text-[#d1fae5] mb-1.5">রং / Colour</span>
                        <div class="flex items-center gap-2.5">
                            <button type="button" class="cm-swatch active" data-color="#0f7644" data-tint="#eef7f2" data-border="#86c5a3" style="background-color:#0f7644;"></button>
                            <button type="button" class="cm-swatch" data-color="#1d4ed8" data-tint="#eff6ff" data-border="#93c5fd" style="background-color:#1d4ed8;"></button>
                            <button type="button" class="cm-swatch" data-color="#dc2626" data-tint="#fef2f2" data-border="#fca5a5" style="background-color:#dc2626;"></button>
                            <button type="button" class="cm-swatch" data-color="#7c3aed" data-tint="#f5f3ff" data-border="#c4b5fd" style="background-color:#7c3aed;"></button>
                            <button type="button" class="cm-swatch" data-color="#0f172a" data-tint="#f1f5f9" data-border="#94a3b8" style="background-color:#0f172a;"></button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Right Preview Column -->
            <div class="lg:col-span-7">
                <div class="cm-card space-y-3">
                    <div class="flex items-center gap-2">
                        <span class="cm-badge">6</span>
                        <h3 class="text-sm font-bold text-white">পূরণ দেখুন ও প্রিন্ট <span class="text-[#22c55e]">(Preview &amp; Print)</span></h3>
                    </div>

                    <div class="flex items-center gap-2">
                        <button id="cm-btnLangBn" type="button" class="cm-lang-pill active">বাংলা ভাষায়</button>
                        <button id="cm-btnLangEn" type="button" class="cm-lang-pill">English Memo</button>
                    </div>

                    <div id="cm-paper" class="cm-paper size-a4">
                        <div id="cm-printable-area" class="cm-frame">
                            <div class="text-center mb-2">
                                <div id="cm-logoWrap" class="hidden justify-center mb-1">
                                    <img id="cm-logoImg" src="" alt="Shop Logo" class="h-10 w-auto object-contain mx-auto" />
                                </div>
                                <div class="flex items-center justify-center gap-1.5">
                                    <span id="cm-defaultIcon" class="inline-flex items-center justify-center w-6 h-6 rounded-full text-white text-xs font-bold" style="background-color:var(--memo-accent);">দ</span>
                                    <h4 id="cm-previewShopName" class="text-xl sm:text-2xl font-bold" style="color:var(--memo-accent);">দোকানের নাম</h4>
                                </div>
                                <p id="cm-previewOwnerName" class="text-[11px] text-gray-600 hidden"></p>
                                <p id="cm-previewShopSub" class="text-[11px] text-gray-600 hidden"></p>
                                <div class="mt-1">
                                    <span id="cm-previewBadgeTitle" class="inline-block px-5 py-0.5 rounded-full text-xs font-bold text-white" style="background-color:var(--memo-accent);">ক্যাশ মেমো</span>
                                </div>
                            </div>

                            <div class="text-xs text-gray-800 space-y-1 mb-2.5">
                                <div class="flex justify-between">
                                    <div><span id="cm-lblBillNo" class="font-semibold">বিলের নং:</span> <span id="cm-previewBillNo" class="font-bold">1</span></div>
                                    <div><span id="cm-lblDate" class="font-semibold">তারিখ:</span> <span id="cm-previewDate" class="font-semibold"></span></div>
                                </div>
                                <div class="flex items-baseline gap-1">
                                    <span id="cm-lblCustName" class="font-semibold whitespace-nowrap">নাম:</span>
                                    <span id="cm-previewCustName" class="cm-dotted flex-1"></span>
                                </div>
                                <div class="grid grid-cols-12 gap-2 items-baseline">
                                    <div class="col-span-7 flex items-baseline gap-1">
                                        <span id="cm-lblCustAddress" class="font-semibold whitespace-nowrap">ঠিকানা:</span>
                                        <span id="cm-previewCustAddress" class="cm-dotted flex-1"></span
