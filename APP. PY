import streamlit as st
from datetime import datetime

# إعدادات اللغة والعنوان
st.set_page_config(page_title="منصة التكوين المهني - الحلويات", layout="wide")

# تخزين حالة اللغة
if 'lang' not in st.session_state:
    st.session_state.lang = 'ar'

# دالة الترجمة البسيطة
def t(ar, fr):
    return ar if st.session_state.lang == 'ar' else fr

# شريط اللغة
col1, col2 = st.columns([8, 1])
with col2:
    if st.button("🇩🇿 عربي / 🇫🇷 Fr"):
        st.session_state.lang = 'fr' if st.session_state.lang == 'ar' else 'ar'
        st.rerun()

# عنوان التطبيق
st.title(t("🧑‍🍳 مذكرة دروس التكوين المهني (صناعة الحلويات)", "🧑‍🍳 Livret de formation professionnelle (Pâtisserie)"))

# نموذج إدخال البيانات
with st.form("lesson_form"):
    st.subheader(t("📝 معلومات الدرس", "📝 Informations de la leçon"))
    
    col1, col2 = st.columns(2)
    with col1:
        unit_name = st.text_input(t("اسم الوحدة (مثال: العجينة المورقة)", "Nom de l'unité (Ex: Pâte feuilletée)"))
        lesson_name = st.text_input(t("اسم الدرس", "Nom de la leçon"))
    with col2:
        duration = st.number_input(t("مدة الطهي (بالدقيقة)", "Temps de cuisson (en minutes)"), min_value=0, step=5)
        final_shape = st.text_input(t("الشكل النهائي وطريقة التقديم", "Forme finale et méthode de présentation"))

    st.subheader(t("🧂 المكونات والأدوات", "🧂 Ingrédients et outils"))
    ingredients = st.text_area(t("المكونات (اكتب كل مكون في سطر)", "Ingrédients (un par ligne)"))
    tools = st.text_area(t("الأدوات المستعملة", "Outils utilisés"))

    st.subheader(t("👨‍🍳 طريقة التحضير", "👨‍🍳 Méthode de préparation"))
    steps = st.text_area(t("خطوات التحضير بالترتيب", "Étapes de préparation dans l'ordre"))

    st.subheader(t("💶 حساب التكلفة التقديرية", "💶 Calcul du coût estimé"))
    cost = st.number_input(t("التكلفة التقديرية للوصفة (بالدينار أو اليورو)", "Coût estimé de la recette"), min_value=0.0, step=100.0)

    st.subheader(t("📄 الامتحان والتصحيح", "📄 Examen et correction"))
    exam = st.text_area(t("أسئلة الامتحان الخاصة بهذه الوحدة", "Questions d'examen pour cette unité"))
    correction = st.text_area(t("التصحيح النموذجي", "Correction type"))

    submitted = st.form_submit_button(t("💾 حفظ الدرس وإنشاء الملف", "💾 Enregistrer la leçon et créer le fichier"))

# إذا تم الضغط على زر الحفظ
if submitted:
    st.success(t("✅ تم حفظ الدرس بنجاح! يمكنك الآن طباعته أو نسخ النص.", "✅ Leçon enregistrée avec succès ! Vous pouvez l'imprimer ou copier le texte."))
    
    # إنشاء محتوى الدرس كملف نصي
    content = f"""
    ==========================================
    {t("اسم الوحدة:", "Unité:")} {unit_name}
    {t("اسم الدرس:", "Leçon:")} {lesson_name}
    {t("مدة الطهي:", "Temps:")} {duration} {t("دقيقة", "min")}
    {t("الشكل النهائي:", "Forme finale:")} {final_shape}
    ==========================================
    {t("المكونات", "Ingrédients")}:
    {ingredients}
    -----------------------
    {t("الأدوات المستعملة", "Outils")}:
    {tools}
    -----------------------
    {t("طريقة التحضير", "Préparation")}:
    {steps}
    -----------------------
    {t("التكلفة التقديرية", "Coût estimé")}: {cost}
    ==========================================
    {t("الامتحان", "Examen")}:
    {exam}
    {t("التصحيح", "Correction")}:
    {correction}
    ==========================================
    """
    
    # عرض المحتوى في الشاشة (لكي ينسخه الأستاذ ويضعه في وورد)
    st.subheader(t("📋 نص الدرس الجاهز للطباعة (يمكنك نسخه وضعه في Word):", "📋 Texte de la leçon prêt à imprimer (copiez-le dans Word):"))
    st.text(content)
