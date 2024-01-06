<p>pip install Flask<br />
&nbsp;</p>

<p>from flask import Flask, render_template, request<br />
from transformers import pipeline</p>

<p>app = Flask(__name__)</p>

<p># Load the text sentiment analysis model<br />
sentiment_analysis = pipeline(&quot;sentiment-analysis&quot;)</p>

<p>@app.route(&#39;/&#39;)<br />
def index():<br />
&nbsp; &nbsp; return render_template(&#39;index.html&#39;)</p>

<p>@app.route(&#39;/analyze&#39;, methods=[&#39;POST&#39;])<br />
def analyze():<br />
&nbsp; &nbsp; if request.method == &#39;POST&#39;:<br />
&nbsp; &nbsp; &nbsp; &nbsp; product_description = request.form[&#39;description&#39;]</p>

<p>&nbsp; &nbsp; &nbsp; &nbsp; # Rate the product description using sentiment analysis<br />
&nbsp; &nbsp; &nbsp; &nbsp; result = sentiment_analysis(product_description)</p>

<p>&nbsp; &nbsp; &nbsp; &nbsp; return render_template(&#39;result.html&#39;, description=product_description, rating=result[0][&#39;label&#39;])</p>

<p>if __name__ == &#39;__main__&#39;:<br />
&nbsp; &nbsp; app.run(debug=True)<br />
pip install transformers<br />
&lt;!DOCTYPE html&gt;<br />
&lt;html lang=&quot;en&quot;&gt;<br />
&lt;head&gt;<br />
&nbsp; &nbsp; &lt;meta charset=&quot;UTF-8&quot;&gt;<br />
&nbsp; &nbsp; &lt;meta http-equiv=&quot;X-UA-Compatible&quot; content=&quot;IE=edge&quot;&gt;<br />
&nbsp; &nbsp; &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;&gt;<br />
&nbsp; &nbsp; &lt;title&gt;Product Description Analyzer&lt;/title&gt;<br />
&lt;/head&gt;<br />
&lt;body&gt;<br />
&nbsp; &nbsp; &lt;h1&gt;Product Description Analyzer&lt;/h1&gt;<br />
&nbsp; &nbsp; &lt;form action=&quot;/analyze&quot; method=&quot;post&quot;&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;label for=&quot;description&quot;&gt;Enter product description:&lt;/label&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;textarea name=&quot;description&quot; rows=&quot;4&quot; cols=&quot;50&quot; required&gt;&lt;/textarea&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;br&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;input type=&quot;submit&quot; value=&quot;Analyze&quot;&gt;<br />
&nbsp; &nbsp; &lt;/form&gt;<br />
&lt;/body&gt;<br />
&lt;/html&gt;</p>

<p>&lt;!DOCTYPE html&gt;<br />
&lt;html lang=&quot;en&quot;&gt;<br />
&lt;head&gt;<br />
&nbsp; &nbsp; &lt;meta charset=&quot;UTF-8&quot;&gt;<br />
&nbsp; &nbsp; &lt;meta http-equiv=&quot;X-UA-Compatible&quot; content=&quot;IE=edge&quot;&gt;<br />
&nbsp; &nbsp; &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;&gt;<br />
&nbsp; &nbsp; &lt;title&gt;Analysis Result&lt;/title&gt;<br />
&lt;/head&gt;<br />
&lt;body&gt;<br />
&nbsp; &nbsp; &lt;h1&gt;Analysis Result&lt;/h1&gt;<br />
&nbsp; &nbsp; &lt;p&gt;&lt;strong&gt;Product Description:&lt;/strong&gt; {{ description }}&lt;/p&gt;<br />
&nbsp; &nbsp; &lt;p&gt;&lt;strong&gt;Rating:&lt;/strong&gt; {{ rating }}&lt;/p&gt;<br />
&lt;/body&gt;<br />
&lt;/html&gt;</p>

<p>python app.py<br />
&nbsp;</p>
