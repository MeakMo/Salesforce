
**Missing ApexDoc comment**

参考：[Documentation | PMD Source Code Analyzer (pmd-code.org)](https://docs.pmd-code.org/pmd-doc-6.39.0/pmd_rules_apex_documentation.html#apexdoc)

解決策：下記のようにコメントを追加する

```java
/**
 * ここはコメントです。
 *
 */
```

**Avoid debug statements since they impact on performance**

参考：[Performance | PMD Source Code Analyzer (pmd-code.org)](https://docs.pmd-code.org/pmd-doc-6.39.0/pmd_rules_apex_performance.html#avoiddebugstatements)

`System.debug()`ステートメントがパフォーマンスに影響を与えるため、避けるべきであることを示しています。

デバッグステートメントがプログラムの実行時間を増加させ、ログファイルを肥大化させる可能性があります。

問題を解決するには：

1. **デバッグステートメントの削除**：コードが正常に動作し、デバッグステートメントが不要であることが確認できた場合、`System.debug()`を削除することが最善の解決策です。
2. **条件付きデバッグステートメントの使用**：デバッグステートメントが必要な場合は、`System.debug()`を条件付きで使用することを検討する。つまり、特定の条件下でのみデバッグステートメントが実行されるようにすること。この対応により、不要なデバッグ出力を減らすことができます。
3. **カスタム設定を使用する**：カスタム設定を使用してデバッグログの出力を制御することも可能です。これにより、デバッグログの出力を動的にオン/オフにすることができます。

**The constant field name 'salesforceKeySet' doesn't match '[A-Z][A-Z0-9_]*’**

参考：[Code Style | PMD Source Code Analyzer (pmd-code.org)](https://docs.pmd-code.org/pmd-doc-6.39.0/pmd_rules_apex_codestyle.html#fieldnamingconventions)

「FieldNamingConventions」ルールに引っかかっています。

このルールは、定数フィールド名が ‘[A-Z][A-Z0-9_]*’ のパターンに一致することを求められています。

例のコードでは、定数フィールド名 ‘salesforceKeySet’ がこのパターンに一致していないため、警告が発生していることです。

解決策：定数フィールド名を大文字のアルファベットとアンダースコア(_)を使用した名前に変更すること。例えば、‘SALESFORCE_KEY_SET’ のようにする。

**Calls to System.debug should specify a logging level.**

参考：[Best Practices | PMD Source Code Analyzer (pmd-code.org)](https://docs.pmd-code.org/pmd-doc-6.39.0/pmd_rules_apex_bestpractices.html#debugsshoulduselogginglevel)

「DebugsShouldUseLoggingLevel」ルールに引っかかっています。

このルールは、System.debugの呼び出しにログレベルを指定することを求められています。

System.debugの呼び出しにログレベルが指定されていない場合、この警告が発生します。

解決策：System.debugの呼び出しにログレベルを指定することです。例えば、`System.debug(LoggingLevel.INFO, 'your message');` **`System.**debug**(LoggingLevel.**ERROR**,** e**.**getMessage**());**` のようにする。

**The class name 'salesforceInfo' doesn't match '[A-Z][a-zA-Z0-9_]*’**

参考：[Code Style | PMD Source Code Analyzer (pmd-code.org)](https://docs.pmd-code.org/pmd-doc-6.39.0/pmd_rules_apex_codestyle.html#classnamingconventions)

「ClassNamingConventions」ルールに引っかかっています。

このルールは、クラス名が ‘[A-Z][a-zA-Z0-9_]*’ のパターンに一致することを求められています。

例のコードでは、クラス名 ‘salesforceInfo’ がこのパターンに一致していないため、警告が発生します。

解決策：クラス名を最初の文字が大文字のアルファベット、その後に小文字または大文字のアルファベット、数字、アンダースコア(_)を使用した名前に変更することです。例えば、‘SalesforceInfo’ のようにする。

**The method 'setPostMap()' has an NCSS line count of 99(数字)**

参考：[Design | PMD Source Code Analyzer (pmd-code.org)](https://docs.pmd-code.org/pmd-doc-6.39.0/pmd_rules_apex_design.html#ncssmethodcount)

「NcssMethodCount」ルールに引っかかっています。

このルールは、メソッドのNCSS行数（Non-Commenting Source Statements、コメント以外のソースステートメントの数）が一定の閾値を超えていることを警告されたものです。

メソッド ‘setPostMap()’ のNCSS行数が99となっており、これが警告の原因となっています。

解決策：メソッドの複雑さを減らし、メソッドをより小さな部分に分割することをお勧められています。具体的には、メソッド内の一部の機能を別のメソッドに移動することで、各メソッドの行数と複雑さを減らすことです。

```java
public class YourClass {
    public void setPostMap() {
        // 一部のコード
        additionalMethod();
        // その他のコード
    }

    private void additionalMethod() {
        // 'setPostMap' メソッドから移動したコード
    }
}

```

**The local variable name 'dt_today' doesn't match '[a-z][a-zA-Z0-9]*’**

参考：[Code Style | PMD Source Code Analyzer (pmd-code.org)](https://docs.pmd-code.org/pmd-doc-6.39.0/pmd_rules_apex_codestyle.html#localvariablenamingconventions)

「LocalVariableNamingConventions」ルールに引っかかっています。

このルールは、ローカル変数名が ‘[a-z][a-zA-Z0-9]*’ のパターンに一致することを要求します。

例のコードでは、ローカル変数名 ‘dt_today’ がこのパターンに一致していないため、警告が発生します。

解決策：ローカル変数名を最初の文字が小文字のアルファベット、その後に小文字または大文字のアルファベット、数字を使用した名前に変更することをお勧められています。例えば、‘dtToday’ のように修正することです。

以下に、修正後のコードの一部を示します：

```java
public class YourClass {
    public void yourMethod() {
        // その他のコード
        Date dtToday = new Date();
        // その他のコード
    }
}
```

**Missing ApexDoc @description**

参考：[Documentation | PMD Source Code Analyzer (pmd-code.org)](https://docs.pmd-code.org/pmd-doc-6.39.0/pmd_rules_apex_documentation.html#apexdoc)

「ApexDoc」ルールに引っかかっています。

このルールは、ApexDocコメントに`@description`タグが含まれていることを求められています。

コードには、ApexDocコメントに`@description`タグが含まれていない場合、警告が発生します。

解決策：メソッドやクラスのApexDocコメントに`@description`タグを追加することで解決されます。`@description`タグの後には、メソッドやクラスの説明を記述します。

```java
/**
 * @description ここにメソッドの説明を書きます
 */
public void yourMethod() {
    // その他のコード
}

```

**Missing ApexDoc @return**

参考：[Documentation | PMD Source Code Analyzer (pmd-code.org)](https://docs.pmd-code.org/pmd-doc-6.39.0/pmd_rules_apex_documentation.html#apexdoc)

「ApexDoc」ルールに引っかかっています。

このルールは、ApexDocコメントに`@return`タグが含まれていることを求められています。

コードには、ApexDocコメントに`@return`タグが含まれていない場合、警告が発生します。

解決策：メソッドのApexDocコメントに`@return`タグを追加することで解決されます。`@return`タグの後には、メソッドの戻り値の説明を記述します。

```java
/**
 * @description ここにメソッドの説明を書きます
 * @param param1 ここにパラメータ1の説明を書きます
 * @param param2 ここにパラメータ2の説明を書きます
 * @return ここに戻り値の説明を書きます
 */
public ReturnType yourMethod(ParamType1 param1, ParamType2 param2) {
    // その他のコード
}
```

****
**Missing or mismatched ApexDoc @param**

参考：[Documentation | PMD Source Code Analyzer (pmd-code.org)](https://docs.pmd-code.org/pmd-doc-6.39.0/pmd_rules_apex_documentation.html#apexdoc)

「ApexDoc」ルールに引っかかっています。

このルールは、ApexDocコメントに`@param`タグが含まれていることを求められています。

コードには、ApexDocコメントに`@param`タグが含まれていない場合、警告が発生します。

解決策：メソッドのApexDocコメントに`@param`タグを追加することで解決されます。`@param`タグの後には、パラメータの説明を記述します。

```java
/**
 * @description ここにメソッドの説明を書きます
 * @param param1 ここにパラメータ1の説明を書きます
 * @param param2 ここにパラメータ2の説明を書きます
 * @return ここに戻り値の説明を書きます
 */
public ReturnType yourMethod(ParamType1 param1, ParamType2 param2) {
    // その他のコード
}
```

**Avoid using if statements without curly braces・IfStmtsMustUseBraces**
参考：[Code Style | PMD Source Code Analyzer (pmd-code.org)](https://docs.pmd-code.org/pmd-doc-6.39.0/pmd_rules_apex_codestyle.html#ifstmtsmustusebraces)

「IfStmtsMustUseBraces」ルールに引っかかっています。

このルールは、if文を使用する際には必ず中括弧（curly braces）を使用することを求められています。

コードには、if文が中括弧なしで使用されている場合、警告が発生します。

解決策：if文の後に続くステートメントを中括弧で囲むことをお勧められます。これにより、コードの可読性が向上し、意図しないエラーの発生を防ぐことができます

```java
if (condition) {
    // ステートメント
}

```

**Avoid using if...else statements without curly braces・IfElseStmtsMustUseBraces**

「IfElseStmtsMustUseBraces」ルールに引っかかっています。

このルールは、if…else文を使用する際には必ず中括弧（curly braces）を使用することを求められています。

コードには、if…else文が中括弧なしで使用されている場合、警告が発生します。

解決策：if…else文の後に続くステートメントを中括弧で囲むことをお勧められます。これにより、コードの可読性が向上し、意図しないエラーの発生を防ぐことができます

以下に、修正後のコードの一部を示します：

```java
if (condition) {
    // ステートメント
} else {
    // ステートメント
}

```
