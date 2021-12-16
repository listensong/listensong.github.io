---
layout: post
title: Kotlin 中的伴随对象 companion object
---

Kotlin 中新增了伴随对象 companion object。

以下为例，这是 Kotlin 中的一份样例代码。

```kotlin
class CompanionShow {
    companion object {
        private var variableLong: Long = 1110L
        internal var variableInt: Int = 220

        @JvmStatic
        val variableUInt: UInt = 3330U

        @JvmField
        val variableFloat: Float = 44440F
        var variableFloatNew: Float = 50505F

        var variableDouble: Double? = null
        const val variableString: String = "HelloWorld"

        fun companionFunction(): Boolean {
            return false
        }

        @JvmStatic
        fun companionFunc() {
            println("What's companion")
        }
    }
}
```

那么与之对应的，相似的 Java 代码长这样：

```java
@Metadata(
   mv = {1, 6, 0},
   k = 1,
   d1 = {"。。。"},
   d2 = {"。。。"}
)
public final class CompanionShow {
   private static long variableLong = 1110L;
   private static int variableInt = 220;
   private static final int variableUInt = 3330;
   @JvmField
   public static final float variableFloat = 44440.0F;
   private static float variableFloatNew = 50505.0F;
   @Nullable
   private static Double variableDouble;
   @NotNull
   public static final String variableString = "HelloWorld";
   @NotNull
   public static final CompanionShow.Companion Companion = 
       new CompanionShow.Companion((DefaultConstructorMarker)null);

   public static final int getVariableUInt_pVg5ArA
       /* $FF was: getVariableUInt-pVg5ArA*/() {
      CompanionShow.Companion var10000 = Companion;
      return variableUInt;
   }

   @JvmStatic
   public static final void companionFunc() {
      Companion.companionFunc();
   }

   @Metadata(
      mv = {1, 6, 0},
      k = 1,
      d1 = {"。。。"},
      d2 = {"。。。"}
   )
   public static final class Companion {
      public final int getVariableInt$app_debug() {
         return CompanionShow.variableInt;
      }

      public final void setVariableInt$app_debug(int var1) {
         CompanionShow.variableInt = var1;
      }

      /** @deprecated */
      // $FF: synthetic method
      @JvmStatic
      public static void getVariableUInt_pVg5ArA$annotations
          /* $FF was: getVariableUInt-pVg5ArA$annotations*/() {
      }

      public final int getVariableUInt_pVg5ArA
          /* $FF was: getVariableUInt-pVg5ArA*/() {
         return CompanionShow.variableUInt;
      }

      public final float getVariableFloatNew() {
         return CompanionShow.variableFloatNew;
      }

      public final void setVariableFloatNew(float var1) {
         CompanionShow.variableFloatNew = var1;
      }

      @Nullable
      public final Double getVariableDouble() {
         return CompanionShow.variableDouble;
      }

      public final void setVariableDouble(@Nullable Double var1) {
         CompanionShow.variableDouble = var1;
      }

      public final boolean companionFunction() {
         return false;
      }

      @JvmStatic
      public final void companionFunc() {
         String var1 = "What's companion";
         System.out.println(var1);
      }

      private Companion() {
      }

      // $FF: synthetic method
      public Companion(DefaultConstructorMarker $constructor_marker) {
         this();
      }
   }
}
```

看起来，还是转成了静态的内部类内部变量了。
