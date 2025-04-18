import React, { useState } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { Select, SelectItem } from "@/components/ui/select";

const products = [ { name: "منتوج 1", image: "https://via.placeholder.com/300x300/FF0000/FFFFFF?text=Product+1", priceMAD: 150 }, { name: "منتوج 2", image: "https://via.placeholder.com/300x300/FF0000/FFFFFF?text=Product+2", priceMAD: 200 }, { name: "منتوج 3", image: "https://via.placeholder.com/300x300/FF0000/FFFFFF?text=Product+3", priceMAD: 300 } ];

const exchangeRates = { MAD: 1, USD: 0.10, EUR: 0.093 };

export default function LokiShop() { const [currency, setCurrency] = useState("MAD");

const formatPrice = (madPrice) => { const converted = (madPrice * exchangeRates[currency]).toFixed(2); switch (currency) { case "USD": return $${converted}; case "EUR": return €${converted}; default: return ${converted} درهم; } };

return ( <div className="min-h-screen bg-black text-red-600 font-sans"> <header className="text-center py-8 text-4xl font-bold">Loki Shop</header>

<div className="flex justify-center mb-4">
    <label className="mr-2 text-white">اختر العملة:</label>
    <select
      value={currency}
      onChange={(e) => setCurrency(e.target.value)}
      className="bg-zinc-900 text-white px-4 py-2 rounded-md"
    >
      <option value="MAD">الدرهم المغربي</option>
      <option value="USD">الدولار الأمريكي</option>
      <option value="EUR">اليورو</option>
    </select>
  </div>

  <main className="grid grid-cols-1 md:grid-cols-3 gap-6 p-4">
    {products.map((product, index) => (
      <Card key={index} className="bg-zinc-900 text-white rounded-2xl shadow-lg">
        <img src={product.image} alt={product.name} className="rounded-t-2xl w-full h-64 object-cover" />
        <CardContent className="p-4 text-center">
          <h2 className="text-xl font-semibold mb-2">{product.name}</h2>
          <p className="text-red-400 font-bold mb-4">{formatPrice(product.priceMAD)}</p>
          <Button className="bg-red-600 hover:bg-red-700 w-full">أضف للسلة</Button>
        </CardContent>
      </Card>
    ))}
  </main>

  <footer className="text-center py-6 text-white text-sm">
    &copy; 2025 Loki Shop - جميع الحقوق محفوظة
  </footer>
</div>

); }

