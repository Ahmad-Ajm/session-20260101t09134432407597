# Specification: FEAT-002 - Events Listing Interface

## المتطلبات الوظيفية
1. يجب أن تعرض الواجهة قائمة الفعاليات الجارية والقادمة فقط.
2. لكل فعالية، يجب عرض:
   - اسم الفعالية
   - تاريخ ووقت الفعالية
   - المدينة/العنوان
   - التصنيف (تعليمي، تقني، مهني...)
   - الجهة المنظمة
   - صورة مصغرة (أو صورة افتراضية)
   - حالة الفعالية (جارية/قادمة)
   - وصف مختصر (اختياري)
3. يجب دعم اللغة العربية بالكامل.
4. يجب أن تكون الواجهة متوافقة مع الهواتف المحمولة (responsive).
5. يجب تحميل البيانات بشكل متدرج (pagination أو infinite scroll).
6. يجب التعامل مع حالات عدم وجود فعاليات أو أخطاء الشبكة.

## المتطلبات غير الوظيفية
- الأداء: يجب ألا يتجاوز زمن تحميل الصفحة 3 ثوانٍ في ظروف الاتصال الضعيف.
- الأمان: لا تعرض بيانات حساسة.
- القابلية للتوسع: دعم إضافة ميزات تصفية أو بحث مستقبلاً.

## نموذج البيانات (Event DTO)
```csharp
public class EventDto
{
    public Guid Id { get; set; }
    public string Name { get; set; }
    public DateTime Date { get; set; }
    public string Time { get; set; }
    public string Location { get; set; }
    public string Category { get; set; }
    public string Organizer { get; set; }
    public string ImageUrl { get; set; }
    public string Status { get; set; } // "جارية" أو "قادمة"
    public string ShortDescription { get; set; }
}
```

## API
- Endpoint: `GET /api/events/list`
- Query params: `page`, `pageSize`
- Response: قائمة فعاليات مع pagination info

## واجهة المستخدم
- Angular component: `events-list`
- يعرض الفعاليات في شكل بطاقات أو قائمة.
- يدعم العربية وواجهة متجاوبة.
- يعرض رسالة "لا توجد فعاليات حالياً" عند عدم وجود بيانات.

## حالات الحافة
- صورة غير متوفرة → عرض صورة افتراضية.
- لا توجد فعاليات → عرض رسالة مناسبة.
- خطأ في الشبكة → عرض رسالة خطأ وإمكانية إعادة المحاولة.
