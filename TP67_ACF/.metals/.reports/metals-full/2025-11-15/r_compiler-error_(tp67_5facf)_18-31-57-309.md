error id: 8A6793B905A720272780FAEC68E8A526
file:///C:/Users/guilh/Documents/00-Master1IL/ACF/TP/TP67_ACF/TP67_ACF/src/main/scala/tp67/tp67.scala
### java.lang.StringIndexOutOfBoundsException: String index out of range: -1

occurred in the presentation compiler.



action parameters:
offset: 1
uri: file:///C:/Users/guilh/Documents/00-Master1IL/ACF/TP/TP67_ACF/TP67_ACF/src/main/scala/tp67/tp67.scala
text:
```scala
*@@
```


presentation compiler configuration:
Scala version: 2.13.16
Classpath:
<WORKSPACE>\.bloop\tp67_acf\bloop-bsp-clients-classes\classes-Metals-Ym2jKKqtRJW7uRTXh88K5w== [exists ], <HOME>\AppData\Local\bloop\cache\semanticdb\com.sourcegraph.semanticdb-javac.0.11.1\semanticdb-javac-0.11.1.jar [exists ], <WORKSPACE>\libJars\tp67.jar [exists ], <HOME>\AppData\Local\Coursier\cache\v1\https\repo1.maven.org\maven2\org\scala-lang\scala-library\2.13.16\scala-library-2.13.16.jar [exists ], <HOME>\AppData\Local\Coursier\cache\v1\https\repo1.maven.org\maven2\org\scala-lang\modules\scala-parser-combinators_2.13\1.1.2\scala-parser-combinators_2.13-1.1.2.jar [exists ]
Options:
-Yrangepos -Xplugin-require:semanticdb




#### Error stacktrace:

```
java.base/java.lang.StringLatin1.charAt(StringLatin1.java:48)
	java.base/java.lang.String.charAt(String.java:1519)
	scala.meta.internal.pc.CompletionProvider.cursorName(CompletionProvider.scala:41)
	scala.meta.internal.pc.CompletionProvider.completions(CompletionProvider.scala:58)
	scala.meta.internal.pc.ScalaPresentationCompiler.$anonfun$complete$1(ScalaPresentationCompiler.scala:236)
	scala.meta.internal.pc.CompilerAccess.withSharedCompiler(CompilerAccess.scala:148)
	scala.meta.internal.pc.CompilerAccess.$anonfun$withInterruptableCompiler$1(CompilerAccess.scala:92)
	scala.meta.internal.pc.CompilerAccess.$anonfun$onCompilerJobQueue$1(CompilerAccess.scala:209)
	scala.meta.internal.pc.CompilerJobQueue$Job.run(CompilerJobQueue.scala:152)
	java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1136)
	java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:635)
	java.base/java.lang.Thread.run(Thread.java:842)
```
#### Short summary: 

java.lang.StringIndexOutOfBoundsException: String index out of range: -1