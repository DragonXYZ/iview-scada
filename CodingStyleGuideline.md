<br>
<h1>Introduction</h1>

This document is a guideline for iView´s contributors. Anyone who submit their code for iView should follow this guideline to keep iView's source code have a unify coding style.<br>
<br>
Most of the standards can be found in C# Coding Style Guide.<br>
<br>
<br>
<h1>Details</h1>

<h2>1. Naming Conventions</h2>
<h3>1.1 Capitalization Styles</h3>
<h4>1.1.1 Pascal Casing</h4>

This convention capitalizes the first character of each word (as in <code>TestCounter</code>).<br>
<h4>1.1.2 Camel Casing</h4>

This convention capitalizes the first character of each word except the first one. E.g. testCounter.<br>
<h4>1.1.3 Upper case</h4>

Only use all upper case for identifiers if it consists of an abbreviation which is one or two characters long, identifiers of three or more characters should use Pascal Casing instead. For Example:<br>
<br>
<pre><code>public class Math<br>
{<br>
    public const PI = ...<br>
    public const E = ...<br>
    public const feigenBaumNumber = ...<br>
}<br>
</code></pre>

<h3>1.2. Naming Guidelines</h3>

Generally the use of underscore characters inside names and naming according to the guidelines for Hungarian notation are considered bad practice.<br>
<br>
Hungarian notation is a defined set of pre and postfixes which are applied to names to reflect the type of the variable. This style of naming was widely used in early Windows programming, but now is obsolete or at least should be considered deprecated. Using Hungarian notation is not allowed if you follow this guide.<br>
<br>
And remember: a good variable name describes the semantic not the type.<br>
<br>
An exception to this rule is GUI code. All fields and variable names that contain GUI elements like button should be postfixed with their type name without abbreviations. For example:<br>
<br>
<pre><code>System.Windows.Forms.Button cancelButton;<br>
System.Windows.Forms.TextBox nameTextBox;<br>
</code></pre>

<h4>1.2.1 Class Naming Guidelines</h4>

Class names must be nouns or noun phrases. Use Pascal Casing see 1.1.1 Do not use any class prefix<br>
<br>
<h4>1.2.2 Interface Naming Guidelines</h4>

Name interfaces with nouns or noun phrases or adjectives describing behavior. For example:<br>
<br>
<pre><code>public interface IComponent<br>
{<br>
}<br>
<br>
public interface IEnumberable<br>
{<br>
}<br>
</code></pre>

Use Pascal Casing (see 1.1.1) Use I as prefix for the name, it is followed by a capital letter (first char of the interface name)<br>
<br>
<h4>1.2.3 Enum Naming Guidelines</h4>

Use Pascal Casing for enum value names and enum type names Don’t prefix (or suffix) a enum type or enum values Use singular names for enums Use plural name for bit fields.<br>
<br>
<h4>1.2.4 <code>ReadOnly</code> and Const Field Names</h4>

Name static fields with nouns, noun phrases or abbreviations for nouns Use Pascal Casing (see 1.1.1)<br>
<br>
<h4>1.2.5 Parameter/non const field Names</h4>

Do use descriptive names, which should be enough to determine the variable meaning and it’s type. But prefer a name that’s based on the parameter’s meaning. Use Camel Casing (see 1.1.2)<br>
<br>
<h4>1.2.6 Variable Names</h4>

Counting variables are preferably called i, j, k, l, m, n when used in 'trivial' counting loops. (see below.) Use Camel Casing (see 1.1.2)<br>
<br>
Variable naming example instead of :<br>
<br>
<pre><code>for (int i = 1; i &lt; num; ++i) <br>
{<br>
    meetsCriteria[i] = true;<br>
}<br>
for (int i = 2; i &lt; num / 2; ++i) <br>
{<br>
    int j = i + i;<br>
    while (j &lt;= num) <br>
    {<br>
        meetsCriteria[j] = false;<br>
        j += i;<br>
    }<br>
}<br>
for (int i = 0; i &lt; num; ++i) <br>
{<br>
    if (meetsCriteria[i]) <br>
    {<br>
        Console.WriteLine(i + " meets criteria");<br>
    }<br>
}<br>
</code></pre>

try intelligent naming :<br>
<br>
<pre><code>for (int primeCandidate = 1; primeCandidate &lt; num; ++primeCandidate)<br>
{<br>
    isPrime[primeCandidate] = true;<br>
}<br>
for (int factor = 2; factor &lt; num / 2; ++factor) <br>
{<br>
    int factorableNumber = factor + factor;<br>
    while (factorableNumber &lt;= num) <br>
    {<br>
        isPrime[factorableNumber] = false;<br>
        factorableNumber += factor;<br>
    }<br>
}<br>
for (int primeCandidate = 0; primeCandidate &lt; num; ++primeCandidate)<br>
{<br>
    if (isPrime[primeCandidate]) <br>
    {<br>
        Console.WriteLine(primeCandidate + " is prime.");<br>
    }<br>
}<br>
</code></pre>

Note: Indexer variables generally should be called i, j, k etc. But in cases like this, it may make sense to reconsider this rule. In general, when the same counters or indexers are reused, give them meaningful names.<br>
<br>
<h4>1.2.7 Method Names</h4>

Name methods with verbs or verb phrases. Use Pascal Casing (see 1.1.2)<br>
<br>
<h4>1.2.8 Property Names</h4>

Name properties using nouns or noun phrases Use Pascal Casing (see 1.1.2) Consider naming a property with the same name as it’s type<br>
<br>
<h4>1.2.9 Event Names</h4>

Use generic event handler <code>EventHandler&lt;T&gt;</code> if possible. Name event handlers with the <code>EventHandler</code> suffix. Use two parameters named sender and e Use Pascal Casing (see 1.1.1) Name event argument classes with the <code>EventArgs</code> suffix. Name event names that have a concept of pre and post using the present and past tense. Consider naming events using a verb.<br>
<br>
<h4>1.2.10 Capitalization summary</h4>

<table><thead><th> Type </th><th> Case </th><th> Notes </th></thead><tbody>
<tr><td> Class/Struct </td><td> Pascal Casing </td><td> - </td></tr>
<tr><td> Interface </td><td> Pascal Casing Starts with I </td><td> - </td></tr>
<tr><td> Enum values </td><td> Pascal Casing </td><td> - </td></tr>
<tr><td> Enum type </td><td> Pascal Casing </td><td> - </td></tr>
<tr><td> Events </td><td> Pascal Casing </td><td> Use <code>EventHandler&lt;T&gt;</code> as prototype if possible </td></tr>
<tr><td> Exception class </td><td> Pascal Casing </td><td> End with Exception </td></tr>
<tr><td> public Fields </td><td> Pascal Casing </td><td> - </td></tr>
<tr><td> Methods </td><td> Pascal Casing </td><td> - </td></tr>
<tr><td> Namespace </td><td> Pascal Casing </td><td> - </td></tr>
<tr><td> Property </td><td> Pascal Casing </td><td> - </td></tr>
<tr><td> Protected/private Fields </td><td> Camel Casing </td><td> - </td></tr>
<tr><td> Parameters </td><td> Camel Casing </td><td> - </td></tr></tbody></table>

<br>
<br>
<br>
<br>
<br>