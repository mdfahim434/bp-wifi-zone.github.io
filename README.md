# BP WiFi ZONE - Firebase সেটআপ (একবারের কাজ)

1. https://console.firebase.google.com এ নতুন প্রজেক্ট খুলুন।
2. Build > Authentication > Get started > Sign-in method > **Email/Password** চালু করুন।
3. Build > Firestore Database > Create database (production mode)। তারপর **Rules** ট্যাবে `firestore.rules` ফাইলের লেখা পেস্ট করে Publish করুন।
4. Authentication > Users > Add user: Email `admin@bpwifi.app`, নিজের পছন্দের পাসওয়ার্ড। তৈরি হলে ওই ইউজারের **User UID** কপি করুন।
5. Firestore > Start collection: Collection ID `admins`, Document ID = ওই UID, একটা ফিল্ড দিন (যেমন `ok` = true)।
6. Project settings > Your apps > Web (</>) অ্যাপ যোগ করে `firebaseConfig` কপি করুন, `index.html` এর শুরুতে `cfg` এর জায়গায় বসান।
7. `index.html` হোস্ট করুন: Firebase Hosting (`firebase deploy`), অথবা Netlify/Vercel/GitHub Pages এ আপলোড করুন।
8. Authentication > Settings > Authorized domains এ আপনার হোস্টিং ডোমেইন যোগ করুন।

লগইন: অ্যাডমিন User ID `admin`। কাস্টমারদের অ্যাডমিন প্যানেল থেকে যোগ করুন (ID + পাসওয়ার্ড দিন)।

## জানা থাকা দরকার
- গ্রাহক মুছলে তার ডেটা মোছে, কিন্তু Firebase Authentication এ ইউজারটা থেকে যায় (Console থেকে হাতে মুছুন)। একই ID আবার ব্যবহার করতে হলে আগে সেটা মুছতে হবে।
- গ্রাহকের পাসওয়ার্ড ভুলে গেলে অ্যাডমিন অ্যাপ থেকে রিসেট করতে পারবে না; Firebase Console থেকে ইউজার মুছে নতুন করে যোগ করতে হবে।
- পেমেন্ট এখন ম্যানুয়াল: গ্রাহক bKash/Nagad এ পাঠাবে, অ্যাডমিন Paid করবে। অটো পেমেন্টের জন্য পেমেন্ট গেটওয়ে লাগবে।
- Firebase এর ফ্রি প্ল্যান (Spark) ছোট ISP ব্যবসার জন্য সাধারণত যথেষ্ট।
