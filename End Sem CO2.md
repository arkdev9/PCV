---


---

<h1 id="pcv-end-sem-co2">PCV End Sem CO2</h1>
<p>Questions:</p>
<ol start="18">
<li>Explain Co-Occurrence matrix.</li>
<li>Define edge and what is the criteria for optimal edge detection.</li>
<li>Outline the effect of noise on edge detection. What are the steps to detect an edge using gradient?</li>
<li>Analyze Local Binary Pattern in context with texture representation.</li>
<li>Human Stereopsis.</li>
<li>Summarize the role of GLCM (Grey Level Co-Occurrence matrix) in texture representation.</li>
<li>What do you mean by Binocular Fusion?</li>
<li>What do you mean by synthesis of texture? Illustrate with suitable example.</li>
<li>Explain the role of derivatives in edge detection. Criticize upon the effect of noise in edge<br>
detection.</li>
<li>Local Binary Pattern (LBP)</li>
<li>Define edge and what is the criteria for optimal edge detection. Write clearly the steps for edge detection in a noisy image with salt and pepper noise.</li>
<li>Explain Local Binary Pattern in context with texture representation.</li>
<li>Explain Local Binary Pattern in context with texture representation.</li>
<li>Explain Fourier transformation.</li>
<li>Criticize on Ringing effect phenomena and compare between smoothening by Gaussian and smoothening by averaging filter</li>
<li>Explain Texture Analysis and give a detailed classification of texture analysis.</li>
<li>Criticize on effect of noise in edge detection.</li>
<li>Convolution theorem in Fourier transformation.</li>
</ol>
<h2 id="explain-co-occurrence-matrix">18 - Explain Co-Occurrence matrix</h2>
<p>Generally speaking, a co-occurrence matrix will have specific entities in rows (ER) and columns (EC). The purpose of this matrix is to present the number of times each ER appears in the same context as each EC. As a consequence, in order to use a co-occurrence matrix, you have to define your entites and the context in which they co-occur.</p>
<p>In NLP, the most classic approach is to define each entity (ie, lines and columns) as a word present in a text, and the context as a sentence.</p>
<p>Consider the following text :<br>
<em>Roses are red. Sky is blue.</em><br>
With the classic approach described before, we’ll have the following matrix :</p>

<table>
<thead>
<tr>
<th></th>
<th>Roses</th>
<th>are</th>
<th>red</th>
<th>Sky</th>
<th>is</th>
<th>blue</th>
</tr>
</thead>
<tbody>
<tr>
<td>Roses</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<td>are</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<td>red</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
</tr>
<tr>
<td>Sky</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>is</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>Blue</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
<td>1</td>
</tr>
</tbody>
</table><p>Here, each cell indicates wether the two items co-occur or not. You may replace it with the number of times it appears, or with a more sophisticated approach. You may also change the entities themselves, by putting nouns in columns and adjective in lines instead of every word.</p>
<p>What are they used for in NLP ?</p>
<p>The most evident use of these matrix is their ability to provide links between notions. Let’s suppose you’re working on products reviews. Let’s also suppose for simplicity that each review is only composed of short sentences. You’ll have something like that :</p>
<p>ProductX is amazing.</p>
<p>I hate productY.<br>
Representing these reviews as one co-occurrence matrix will enable you associate products with appreciations.</p>
<h2 id="define-edge-and-what-is-the-criteria-for-optimal-edge-detection">19 - Define edge and what is the criteria for optimal edge detection</h2>
<p><strong>Definition of edges</strong></p>
<ul>
<li>Edges are significant local changes of intensity in an image.</li>
<li>Edges typically occur on the boundary between two different regions in an image.</li>
</ul>
<p><strong>Goal of edge detection</strong></p>
<ul>
<li>Produce a line drawing of a scene from an image of that scene.</li>
<li>Important features can be extracted from the edges of an image (e.g., corners, lines, curves).</li>
<li>These features are used by higher-level computer vision algorithms (e.g., recognition).</li>
</ul>
<p><strong>The four steps of edge detection</strong></p>
<p><em>Smoothing</em>: suppress as much noise as possible, without destroying the true edges.</p>
<p><em>Enhancement</em>: apply a filter to enhance the quality of the edges in the image (sharpening).</p>
<p><em>Detection</em>: determine which edge pixels should be discarded as noise and which should be retained (usually, thresholding provides the criterion used for detection).</p>
<p><em>Localization</em>: determine the exact location of an edge (sub-pixel resolution might be required for some applications, that is, estimate the location of an edge to better than the spacing between pixels). Edge thinning and linking are usually required in this step</p>
<p><strong>Good detection</strong>: the optimal detector must minimize the probability of false positives (detecting spurious edges caused by noise), as well as that of false neg- atives (missing real edges).<br>
<strong>Good localization</strong>: the edges detected must be as close as possible to the true edges.<br>
Single response constraint: the detector must return one point only for each true edge point; that is, minimize the number of local maxima around the true edge (created by noise).</p>
<h2 id="outline-the-effect-of-noise-on-edge-detection.-what-are-the-steps-to-detect-an-edge-using-gradient">20 - Outline the effect of noise on edge detection. What are the steps to detect an edge using gradient</h2>
<p><strong>Derivatives are strongly affected by noise</strong></p>
<ul>
<li>Reason: image noise results in pixels that look very different from their neighbors</li>
<li>The larger the noise - the stronger the response</li>
</ul>
<p><strong>What is to be done?</strong></p>
<ul>
<li>Neighboring pixels look alike</li>
<li>Pixel along an edge look alike</li>
<li>Image smoothing should help</li>
<li>Force pixels different to their neighbors (possibly noise) to look like neighbors</li>
</ul>
<p><strong>Definition of the gradient</strong></p>
<ul>
<li>The gradient is a vector which has certain magnitude and direction:</li>
</ul>
<p><span class="katex--display"><span class="katex-display"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi mathvariant="normal">∇</mi><mi>f</mi><mo>=</mo><mrow><mo fence="true">(</mo><mtable rowspacing="0.15999999999999992em" columnspacing="1em" rowlines="solid none solid"><mtr><mtd><mstyle scriptlevel="0" displaystyle="false"><mrow><mi>δ</mi><mi>f</mi></mrow></mstyle></mtd></mtr><mtr><mtd><mstyle scriptlevel="0" displaystyle="false"><mrow><mi>δ</mi><mi>x</mi></mrow></mstyle></mtd></mtr><mtr><mtd><mstyle scriptlevel="0" displaystyle="false"><mrow><mi>δ</mi><mi>f</mi></mrow></mstyle></mtd></mtr><mtr><mtd><mstyle scriptlevel="0" displaystyle="false"><mrow><mi>δ</mi><mi>y</mi></mrow></mstyle></mtd></mtr></mtable><mo fence="true">)</mo></mrow></mrow><annotation encoding="application/x-tex">
\nabla f =  \begin{pmatrix}
\delta f \\ \hline
\delta x \\
\delta f \\ \hline
\delta y \end{pmatrix}
</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 0.8888799999999999em; vertical-align: -0.19444em;"></span><span class="mord">∇</span><span class="mord mathdefault" style="margin-right: 0.10764em;">f</span><span class="mspace" style="margin-right: 0.2777777777777778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.2777777777777778em;"></span></span><span class="base"><span class="strut" style="height: 4.80006em; vertical-align: -2.15003em;"></span><span class="minner"><span class="mopen"><span class="delimsizing mult"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 2.6500299999999997em;"><span class="" style="top: -1.6499900000000003em;"><span class="pstrut" style="height: 3.1550000000000002em;"></span><span class="delimsizinginner delim-size4"><span class="">⎝</span></span></span><span class="" style="top: -2.805em;"><span class="pstrut" style="height: 3.1550000000000002em;"></span><span class="delimsizinginner delim-size4"><span class="">⎜</span></span></span><span class="" style="top: -3.4050100000000003em;"><span class="pstrut" style="height: 3.1550000000000002em;"></span><span class="delimsizinginner delim-size4"><span class="">⎜</span></span></span><span class="" style="top: -4.65003em;"><span class="pstrut" style="height: 3.1550000000000002em;"></span><span class="delimsizinginner delim-size4"><span class="">⎛</span></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 2.15003em;"><span class=""></span></span></span></span></span></span><span class="mord"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 2.6500000000000004em;"><span class="" style="top: -4.65em;"><span class="pstrut" style="height: 4.65em;"></span><span class="mtable"><span class="col-align-c"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 2.6500000000000004em;"><span class="" style="top: -4.8100000000000005em;"><span class="pstrut" style="height: 3em;"></span><span class="mord"><span class="mord mathdefault" style="margin-right: 0.03785em;">δ</span><span class="mord mathdefault" style="margin-right: 0.10764em;">f</span></span></span><span class="" style="top: -3.61em;"><span class="pstrut" style="height: 3em;"></span><span class="mord"><span class="mord mathdefault" style="margin-right: 0.03785em;">δ</span><span class="mord mathdefault">x</span></span></span><span class="" style="top: -2.4099999999999997em;"><span class="pstrut" style="height: 3em;"></span><span class="mord"><span class="mord mathdefault" style="margin-right: 0.03785em;">δ</span><span class="mord mathdefault" style="margin-right: 0.10764em;">f</span></span></span><span class="" style="top: -1.2099999999999997em;"><span class="pstrut" style="height: 3em;"></span><span class="mord"><span class="mord mathdefault" style="margin-right: 0.03785em;">δ</span><span class="mord mathdefault" style="margin-right: 0.03588em;">y</span></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 2.1500000000000004em;"><span class=""></span></span></span></span></span></span></span><span class="" style="top: -3.7000000000000006em;"><span class="pstrut" style="height: 4.65em;"></span><span class="hline" style="border-bottom-width: 0.05em;"></span></span><span class="" style="top: -6.1000000000000005em;"><span class="pstrut" style="height: 4.65em;"></span><span class="hline" style="border-bottom-width: 0.05em;"></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 2.1500000000000004em;"><span class=""></span></span></span></span></span><span class="mclose"><span class="delimsizing mult"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 2.6500299999999997em;"><span class="" style="top: -1.6499900000000003em;"><span class="pstrut" style="height: 3.1550000000000002em;"></span><span class="delimsizinginner delim-size4"><span class="">⎠</span></span></span><span class="" style="top: -2.805em;"><span class="pstrut" style="height: 3.1550000000000002em;"></span><span class="delimsizinginner delim-size4"><span class="">⎟</span></span></span><span class="" style="top: -3.4050100000000003em;"><span class="pstrut" style="height: 3.1550000000000002em;"></span><span class="delimsizinginner delim-size4"><span class="">⎟</span></span></span><span class="" style="top: -4.65003em;"><span class="pstrut" style="height: 3.1550000000000002em;"></span><span class="delimsizinginner delim-size4"><span class="">⎞</span></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 2.15003em;"><span class=""></span></span></span></span></span></span></span></span></span></span></span></span><br>
<span class="katex--display"><span class="katex-display"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi>m</mi><mi>a</mi><mi>g</mi><mi>n</mi><mo stretchy="false">(</mo><mi mathvariant="normal">∇</mi><mi>f</mi><mo stretchy="false">)</mo><mo>=</mo><msqrt><mrow><mo stretchy="false">(</mo><mfrac><mrow><mi>δ</mi><mi>f</mi></mrow><mrow><mi>δ</mi><mi>x</mi></mrow></mfrac><msup><mo stretchy="false">)</mo><mn>2</mn></msup><mo>+</mo><mo stretchy="false">(</mo><mfrac><mrow><mi>δ</mi><mi>f</mi></mrow><mrow><mi>δ</mi><mi>y</mi></mrow></mfrac><msup><mo stretchy="false">)</mo><mn>2</mn></msup></mrow></msqrt><mo>=</mo><msqrt><mrow><msubsup><mi>M</mi><mi>x</mi><mn>2</mn></msubsup><mo>+</mo><msubsup><mi>M</mi><mi>y</mi><mn>2</mn></msubsup></mrow></msqrt></mrow><annotation encoding="application/x-tex">
magn(\nabla f) = \sqrt {(\frac {\delta f} {\delta x})^2 + (\frac {\delta f} {\delta y})^2}  = \sqrt {M_x^2 + M_y^2}
</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathdefault">m</span><span class="mord mathdefault">a</span><span class="mord mathdefault" style="margin-right: 0.03588em;">g</span><span class="mord mathdefault">n</span><span class="mopen">(</span><span class="mord">∇</span><span class="mord mathdefault" style="margin-right: 0.10764em;">f</span><span class="mclose">)</span><span class="mspace" style="margin-right: 0.2777777777777778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.2777777777777778em;"></span></span><span class="base"><span class="strut" style="height: 3.04em; vertical-align: -1.1606250000000005em;"></span><span class="mord sqrt"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 1.8793749999999996em;"><span class="svg-align" style="top: -5em;"><span class="pstrut" style="height: 5em;"></span><span class="mord" style="padding-left: 1em;"><span class="mopen">(</span><span class="mord"><span class="mopen nulldelimiter"></span><span class="mfrac"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 1.3714399999999998em;"><span class="" style="top: -2.314em;"><span class="pstrut" style="height: 3em;"></span><span class="mord"><span class="mord mathdefault" style="margin-right: 0.03785em;">δ</span><span class="mord mathdefault">x</span></span></span><span class="" style="top: -3.23em;"><span class="pstrut" style="height: 3em;"></span><span class="frac-line" style="border-bottom-width: 0.04em;"></span></span><span class="" style="top: -3.677em;"><span class="pstrut" style="height: 3em;"></span><span class="mord"><span class="mord mathdefault" style="margin-right: 0.03785em;">δ</span><span class="mord mathdefault" style="margin-right: 0.10764em;">f</span></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.686em;"><span class=""></span></span></span></span></span><span class="mclose nulldelimiter"></span></span><span class="mclose"><span class="mclose">)</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.740108em;"><span class="" style="top: -2.9890000000000003em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span><span class="mspace" style="margin-right: 0.2222222222222222em;"></span><span class="mbin">+</span><span class="mspace" style="margin-right: 0.2222222222222222em;"></span><span class="mopen">(</span><span class="mord"><span class="mopen nulldelimiter"></span><span class="mfrac"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 1.3714399999999998em;"><span class="" style="top: -2.314em;"><span class="pstrut" style="height: 3em;"></span><span class="mord"><span class="mord mathdefault" style="margin-right: 0.03785em;">δ</span><span class="mord mathdefault" style="margin-right: 0.03588em;">y</span></span></span><span class="" style="top: -3.23em;"><span class="pstrut" style="height: 3em;"></span><span class="frac-line" style="border-bottom-width: 0.04em;"></span></span><span class="" style="top: -3.677em;"><span class="pstrut" style="height: 3em;"></span><span class="mord"><span class="mord mathdefault" style="margin-right: 0.03785em;">δ</span><span class="mord mathdefault" style="margin-right: 0.10764em;">f</span></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.8804400000000001em;"><span class=""></span></span></span></span></span><span class="mclose nulldelimiter"></span></span><span class="mclose"><span class="mclose">)</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.740108em;"><span class="" style="top: -2.9890000000000003em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span></span></span></span></span></span></span><span class="" style="top: -3.8393749999999995em;"><span class="pstrut" style="height: 5em;"></span><span class="hide-tail" style="min-width: 1.02em; height: 3.08em;"><svg width="400em" height="3.08em" viewBox="0 0 400000 3240" preserveAspectRatio="xMinYMin slice"><path d="M473,2793c339.3,-1799.3,509.3,-2700,510,-2702
c3.3,-7.3,9.3,-11,18,-11H400000v40H1017.7s-90.5,478,-276.2,1466c-185.7,988,
-279.5,1483,-281.5,1485c-2,6,-10,9,-24,9c-8,0,-12,-0.7,-12,-2c0,-1.3,-5.3,-32,
-16,-92c-50.7,-293.3,-119.7,-693.3,-207,-1200c0,-1.3,-5.3,8.7,-16,30c-10.7,
21.3,-21.3,42.7,-32,64s-16,33,-16,33s-26,-26,-26,-26s76,-153,76,-153s77,-151,
77,-151c0.7,0.7,35.7,202,105,604c67.3,400.7,102,602.7,104,606z
M1001 80H400000v40H1017z"></path></svg></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 1.1606250000000005em;"><span class=""></span></span></span></span></span><span class="mspace" style="margin-right: 0.2777777777777778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.2777777777777778em;"></span></span><span class="base"><span class="strut" style="height: 1.84em; vertical-align: -0.6276249999999999em;"></span><span class="mord sqrt"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 1.2123750000000002em;"><span class="svg-align" style="top: -3.8em;"><span class="pstrut" style="height: 3.8em;"></span><span class="mord" style="padding-left: 1em;"><span class="mord"><span class="mord mathdefault" style="margin-right: 0.10903em;">M</span><span class="msupsub"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 0.740108em;"><span class="" style="top: -2.4530000000000003em; margin-left: -0.10903em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mathdefault mtight">x</span></span></span><span class="" style="top: -2.9890000000000003em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.247em;"><span class=""></span></span></span></span></span></span><span class="mspace" style="margin-right: 0.2222222222222222em;"></span><span class="mbin">+</span><span class="mspace" style="margin-right: 0.2222222222222222em;"></span><span class="mord"><span class="mord mathdefault" style="margin-right: 0.10903em;">M</span><span class="msupsub"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 0.7401079999999999em;"><span class="" style="top: -2.4530000000000003em; margin-left: -0.10903em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mathdefault mtight" style="margin-right: 0.03588em;">y</span></span></span><span class="" style="top: -2.989em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight">2</span></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.383108em;"><span class=""></span></span></span></span></span></span></span></span><span class="" style="top: -3.1723749999999997em;"><span class="pstrut" style="height: 3.8em;"></span><span class="hide-tail" style="min-width: 1.02em; height: 1.8800000000000001em;"><svg width="400em" height="1.8800000000000001em" viewBox="0 0 400000 1944" preserveAspectRatio="xMinYMin slice"><path d="M1001,80H400000v40H1013.1s-83.4,268,-264.1,840c-180.7,
572,-277,876.3,-289,913c-4.7,4.7,-12.7,7,-24,7s-12,0,-12,0c-1.3,-3.3,-3.7,-11.7,
-7,-25c-35.3,-125.3,-106.7,-373.3,-214,-744c-10,12,-21,25,-33,39s-32,39,-32,39
c-6,-5.3,-15,-14,-27,-26s25,-30,25,-30c26.7,-32.7,52,-63,76,-91s52,-60,52,-60
s208,722,208,722c56,-175.3,126.3,-397.3,211,-666c84.7,-268.7,153.8,-488.2,207.5,
-658.5c53.7,-170.3,84.5,-266.8,92.5,-289.5c4,-6.7,10,-10,18,-10z
M1001 80H400000v40H1013z"></path></svg></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.6276249999999999em;"><span class=""></span></span></span></span></span></span></span></span></span></span><br>
<span class="katex--display"><span class="katex-display"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi>d</mi><mi>i</mi><mi>r</mi><mo stretchy="false">(</mo><mi mathvariant="normal">∇</mi><mi>f</mi><mo stretchy="false">)</mo><mo>=</mo><mi>t</mi><mi>a</mi><msup><mi>n</mi><mrow><mo>−</mo><mn>1</mn></mrow></msup><mo stretchy="false">(</mo><mfrac><msub><mi>M</mi><mi>y</mi></msub><msub><mi>M</mi><mi>x</mi></msub></mfrac><mo stretchy="false">)</mo></mrow><annotation encoding="application/x-tex">
dir(\nabla f) = tan^{-1}(\frac {M_y} {M_x})
</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathdefault">d</span><span class="mord mathdefault">i</span><span class="mord mathdefault" style="margin-right: 0.02778em;">r</span><span class="mopen">(</span><span class="mord">∇</span><span class="mord mathdefault" style="margin-right: 0.10764em;">f</span><span class="mclose">)</span><span class="mspace" style="margin-right: 0.2777777777777778em;"></span><span class="mrel">=</span><span class="mspace" style="margin-right: 0.2777777777777778em;"></span></span><span class="base"><span class="strut" style="height: 2.19633em; vertical-align: -0.8360000000000001em;"></span><span class="mord mathdefault">t</span><span class="mord mathdefault">a</span><span class="mord"><span class="mord mathdefault">n</span><span class="msupsub"><span class="vlist-t"><span class="vlist-r"><span class="vlist" style="height: 0.864108em;"><span class="" style="top: -3.113em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mtight"><span class="mord mtight">−</span><span class="mord mtight">1</span></span></span></span></span></span></span></span></span><span class="mopen">(</span><span class="mord"><span class="mopen nulldelimiter"></span><span class="mfrac"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 1.36033em;"><span class="" style="top: -2.3139999999999996em;"><span class="pstrut" style="height: 3em;"></span><span class="mord"><span class="mord"><span class="mord mathdefault" style="margin-right: 0.10903em;">M</span><span class="msupsub"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 0.151392em;"><span class="" style="top: -2.5500000000000003em; margin-left: -0.10903em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mathdefault mtight">x</span></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.15em;"><span class=""></span></span></span></span></span></span></span></span><span class="" style="top: -3.23em;"><span class="pstrut" style="height: 3em;"></span><span class="frac-line" style="border-bottom-width: 0.04em;"></span></span><span class="" style="top: -3.677em;"><span class="pstrut" style="height: 3em;"></span><span class="mord"><span class="mord"><span class="mord mathdefault" style="margin-right: 0.10903em;">M</span><span class="msupsub"><span class="vlist-t vlist-t2"><span class="vlist-r"><span class="vlist" style="height: 0.15139200000000003em;"><span class="" style="top: -2.5500000000000003em; margin-left: -0.10903em; margin-right: 0.05em;"><span class="pstrut" style="height: 2.7em;"></span><span class="sizing reset-size6 size3 mtight"><span class="mord mathdefault mtight" style="margin-right: 0.03588em;">y</span></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.286108em;"><span class=""></span></span></span></span></span></span></span></span></span><span class="vlist-s">​</span></span><span class="vlist-r"><span class="vlist" style="height: 0.8360000000000001em;"><span class=""></span></span></span></span></span><span class="mclose nulldelimiter"></span></span><span class="mclose">)</span></span></span></span></span></span></p>
<ul>
<li>To save computations, the magnitude of gradient is usually approxi- mated by:</li>
</ul>
<p><span class="katex--display"><span class="katex-display"><span class="katex"><span class="katex-mathml"><math><semantics><mrow><mi>m</mi><mi>a</mi><mi>g</mi><mi>n</mi><mo stretchy="false">(</mo><mi mathvariant="normal">∇</mi><mi>f</mi><mo stretchy="false">)</mo><mo>≈</mo><mi mathvariant="normal">∣</mi><mi>M</mi><mi>x</mi><mi mathvariant="normal">∣</mi><mo>+</mo><mi mathvariant="normal">∣</mi><mi>M</mi><mi>y</mi><mi mathvariant="normal">∣</mi></mrow><annotation encoding="application/x-tex">magn(∇f) ≈ |Mx| + |My|</annotation></semantics></math></span><span class="katex-html" aria-hidden="true"><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord mathdefault">m</span><span class="mord mathdefault">a</span><span class="mord mathdefault" style="margin-right: 0.03588em;">g</span><span class="mord mathdefault">n</span><span class="mopen">(</span><span class="mord">∇</span><span class="mord mathdefault" style="margin-right: 0.10764em;">f</span><span class="mclose">)</span><span class="mspace" style="margin-right: 0.2777777777777778em;"></span><span class="mrel">≈</span><span class="mspace" style="margin-right: 0.2777777777777778em;"></span></span><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord">∣</span><span class="mord mathdefault" style="margin-right: 0.10903em;">M</span><span class="mord mathdefault">x</span><span class="mord">∣</span><span class="mspace" style="margin-right: 0.2222222222222222em;"></span><span class="mbin">+</span><span class="mspace" style="margin-right: 0.2222222222222222em;"></span></span><span class="base"><span class="strut" style="height: 1em; vertical-align: -0.25em;"></span><span class="mord">∣</span><span class="mord mathdefault" style="margin-right: 0.10903em;">M</span><span class="mord mathdefault" style="margin-right: 0.03588em;">y</span><span class="mord">∣</span></span></span></span></span></span></p>
<h2 id="analyze-local-binary-pattern-in-context-with-texture-representation">21 - Analyze Local Binary Pattern in context with texture representation</h2>
<p>Local Binary Patterns, or LBPs for short, are a texture descriptor</p>
<p><img src="https://pyimagesearch.com/wp-content/uploads/2015/12/lbp_thresholding.jpg" alt="Image"><br>
<em>The first step in constructing a LBP is to take the 8 pixel neighborhood surrounding a center pixel and threshold it to construct a set of 8 binary digits.</em></p>
<p>The first step in constructing the LBP texture descriptor is to convert the image to grayscale. For each pixel in the grayscale image, we select a neighborhood of size <em>r</em> surrounding the center pixel. A LBP value is then calculated for this center pixel and stored in the output 2D array with the same width and height as the input image.</p>
<p>From there, we need to calculate the LBP value for the center pixel. We can start from any neighboring pixel and work our way clockwise or counter-clockwise, but our ordering must be kept <em>consistent</em> for all pixels in our image and all images in our dataset. Given a <em>3 x 3</em> neighborhood, we thus have 8 neighbors that we must perform a binary test on. The results of this binary test are stored in an 8-bit array, which we then convert to decimal, like this:</p>
<p><img src="https://pyimagesearch.com/wp-content/uploads/2015/12/lbp_calculation.jpg" alt="Image"><br>
<em>Taking the 8-bit binary neighborhood of the center pixel and converting it into a decimal representation.</em></p>
<p><img src="https://pyimagesearch.com/wp-content/uploads/2015/12/lbp_to_output.jpg" alt="Image"></p>
<p>The last step is to compute a histogram over the output LBP array. Since a <em>3 x 3</em> neighborhood has <em>2 ^ 8 = 256</em> possible patterns, our LBP 2D array thus has a <em>minimum value of 0</em> and a <em>maximum value of 255</em>, allowing us to construct a 256-bin histogram of LBP codes as our final feature vector.</p>
<p>A primary benefit of this original LBP implementation is that we can capture extremely fine-grained details in the image.</p>
<h2 id="human-stereopsis">22 - Human Stereopsis</h2>
<p>Human Beings with Two Eyes that Work Together Have Stereovision. Each eye captures its own view and the two separate images are sent on to the brain for processing. When the two images arrive simultaneously in the back of the brain, they are united into one picture. The mind combines the two images by matching up the similarities and adding in the small differences. The small differences between the two images add up to a big difference in the final picture! The combined image is more than the sum of its parts. It is a three-dimensional <em>stereo</em> picture. Helps with depth perception.</p>
<p><strong>Stereo Vision Has Many Advantages</strong></p>
<ul>
<li>Baseball player</li>
<li>Waitress</li>
<li>Driver</li>
<li>Architect</li>
<li>Surgeon</li>
<li>Dentist</li>
</ul>
<h2 id="summarize-the-role-of-glcm-grey-level-co-occurrence-matrix-in-texture-representation">23 - Summarize the role of GLCM (Grey Level Co-Occurrence matrix) in texture representation</h2>
<p>A statistical method of examining texture that considers the spatial relationship of pixels is the gray-level co-occurrence matrix (GLCM), also known as the gray-level spatial dependence matrix. The GLCM functions characterize the texture of an image by calculating how often pairs of pixel with specific values and in a specified spatial relationship occur in an image, creating a GLCM, and then extracting statistical measures from this matrix.</p>
<p>Texture classification is concerned with identifying a given textured region from a given set of texture classes. GLCM is a statistical approach that is widely used.</p>
<p><strong>Algorithm</strong></p>
<ul>
<li>Count all pairs of pixels in which the first pixel has a value i, and its matching pair displaced from the first pixel by d has a value of j.</li>
<li>This count is entered in the ith row and jthcolumn of the matrix Pd[i,j]</li>
<li>Note that Pd[i,j] is not symmetric, since the number of pairs of pixels having gray levels [i,j] does not necessarily equal the number of pixel pairs having gray levels [j,i].</li>
</ul>
<h2 id="what-do-you-mean-by-binocular-fusion">24 - What do you mean by Binocular Fusion?</h2>
<p>Merging of slightly different images from the two eyes, arising from <strong>binocular</strong> disparity, into a single stereoscopic perception. Also called simply <strong>fusion</strong> or <strong>binocular</strong> interaction.</p>
<p>When images in the two eyes are sufficiently similar, they are ‘fused’. Fusion has motor (vergence) and sensory components. When vergence is prevented, sensory ‘fusion’ of disparate images still occurs, but the nature of this fusion has received curiously little attention. Summation of signals from the two eyes is fairly well understood and seems the obvious basis for fusion.</p>
<p><strong>Advantages</strong></p>
<ul>
<li>Optical defects in one eye are made less obvious by the normal image in the other</li>
<li>Defective vision in one part of the visual field is masked because the same image falls on the functioning area of the other retina</li>
<li>Field of vision is larger</li>
<li>Presence of stereopsis</li>
</ul>
<h2 id="what-do-you-mean-by-synthesis-of-texture-illustrate-with-suitable-example">25 - What do you mean by synthesis of texture? Illustrate with suitable example</h2>
<p>Definition</p>
<ul>
<li>Texture synthesis is defined as a process of producing new textures that are perceptually equivalent to the input texture</li>
<li>Texture synthesis is important for fast scene generation, image inpainting  and texture restoration</li>
</ul>
<p>Applications</p>
<ul>
<li>3D computer graphics</li>
<li>post-production of films</li>
<li>Image painting</li>
</ul>
<p>Tiling produces jarring edges that are easily noticeable. Synthesis overcomes this.</p>
<h2 id="explain-the-role-of-derivatives-in-edge-detection.-criticize-upon-the-effect-of-noise-in-edge-detection">26 - Explain the role of derivatives in edge detection. Criticize upon the effect of noise in edge detection</h2>
<p>Calculus describes changes of continuous functions using derivatives. An image is a 2D function, so operators describing edges are expressed using partial derivatives.</p>
<p>Points which lie on an edge can be detected by:</p>
<ol>
<li>detecting local maxima or minima of the first derivative</li>
<li>detecting the zero-crossing of the second derivative</li>
</ol>
<p>Generally 2nd derivative is more sensitive to noise than 1st derivative. The 2nd derivative is usually accompanied by zero crossing detection, so it works better when grey level transitions are smooth. When the noise level is high, the gray level fluctuates and may result in many zero crossings.</p>
<p>Disadvantages are Senstivity to noise and Inaccurate.</p>
<h2 id="local-binary-pattern-lbp">27 - Local Binary Pattern (LBP)</h2>
<p>See question 21</p>
<h2 id="see-question--19">28 - See question  19</h2>
<h2 id="see-question-21">29 - See question 21</h2>
<h2 id="see-question-21-1">30 - See question 21</h2>
<h2 id="fourier-transformation">31 - Fourier Transformation</h2>
<p>The <strong>Fourier Transform</strong> is an important image processing tool which is used to decompose an image into its sine and cosine components. The output of the transformation represents the image in the <strong>Fourier</strong> or frequency domain, while the input image is the spatial domain equivalent.</p>
<p>At a conceptual level, the Fourier Transform tells you what is happening in the image in terms the frequencies of those sinusoids. For example, if you have a picture of a plain wall, the values of the pixels change very little as you go from left to right or from top to bottom. In the frequency domain that means that your image contains low frequencies, but no high frequencies.</p>
<p>FFT is used extensively in image processing and computer vision. For example, convolution, a fundamental image processing operation, can be done much faster by using the FFT. The Wiener filter, used for image deblurring, is defined in therms of the Fourier transform. But more importantly, even when the Fourier transform is not used directly, it provides a very useful framework for reasoning about the image processing operations.</p>
<h2 id="criticize-on-ringing-effect-phenomena-and-compare-between-smoothening-by-gaussian-and-smoothening-by-averaging-filter">32 - Criticize on Ringing effect phenomena and compare between smoothening by Gaussian and smoothening by averaging filter</h2>
<p><strong>Ringing effect</strong> so known as Gibbs phenomenon in mathematical methods of image processing is the annoying effect in images and video appeared as rippling artifact near sharp edges. This effect is caused by distortion or loss of high frequency information in image.</p>
<p>Mean filter (rectangular kernel) is optimal for reducing random noise in spatial domain (image space). However Mean filter is the worst filter for frequency domain, with little ability to separate one band of frequencies from another. Gaussian filter has better performance in frequency domain.</p>
<p>Mean filter is the least effective among low-pass filters. Ideally it should stop high frequencies and pass only low frequencies. In reality it passes many high frequencies and stops some of the low frequencies (slow roll-off and poor stopband attenuation).</p>
<p>What it means in practice? Mean filter is fast and probably the best solution if you want to remove noise from image. It is bad solution if you want to separate frequencies present in the image.</p>
<p>The interesting thing is that you can implement Gaussian filter using Mean filter. If you apply Mean filter twice to the image you get the same result as applying triangular kernel filter. If you apply Mean filter 4 times to the image you get the same result as applying Gaussian kernel filter.</p>
<p>Gaussian filter uses convolution and is very slow. If you implement Mean filter using recursive formula it will run like lightning. Applying Mean filter many times you can speed up Gaussian implementation 1000 times.</p>
<p>Mean filter and Gaussian filter give similar results when removing noise from image. Gaussian filter is much better at separating frequencies. The best filter for this task is Windowed Sinc filter.</p>
<h2 id="explain-texture-analysis-and-give-a-detailed-classification-of-texture-analysis">33 - Explain Texture Analysis and give a detailed classification of texture analysis</h2>
<p>What is Texture?</p>
<ul>
<li>Texture is a feature used to partition images into regions of interest and to classify those regions.</li>
<li>Texture provides information in the spatial arrangement of colours or intensities in an image.</li>
<li>Texture is characterized by the spatial distribution of intensity levels in a neighborhood.</li>
</ul>
<p>Texture consists of texture primitives or texture elements, sometimes called texels</p>
<ul>
<li>Texture can be described as fine, coarse, grained, smooth, etc.</li>
<li>Such features are found in the tone and structure of a texture.</li>
<li>Tone is based on pixel intensity properties in the texel, whilst structure represents the spatial relationship between texels.</li>
</ul>
<p>There are two primary issues in texture analysis</p>
<ul>
<li>texture classification</li>
<li>texture segmentation</li>
</ul>
<p>Texture classification is concerned with identifying a given textured region from a given set of texture classes.</p>
<ul>
<li>Each of these regions has unique texture characteristics.</li>
<li>Statistical methods are extensively used. e.g. GLCM, contrast, entropy, homogeneity</li>
</ul>
<p>There are three approaches to defining exactly what a texture is:</p>
<ul>
<li><em>Structural</em>: texture is a set of primitive texels in some regular or repeated relationship.</li>
<li><em>Statistical</em>: texture is a quantitative measure of the arrangement of intensities in a region. This set of measurements is called a feature vector.</li>
<li><em>Modelling</em>: texture modelling techniques involve constructing models to specify textures.</li>
</ul>
<h2 id="see-question-26">34 - See Question 26</h2>
<h2 id="convolution-theorem-in-fourier-transformation">35 - Convolution theorem in Fourier transformation</h2>
<p>The convolution theorem is a fundamental property of the Fourier transform. It is often stated like</p>
<blockquote>
<p>“Convolution in time domain equals multiplication in frequency domain”</p>
</blockquote>
<p>The convolution theorem connects the time- and frequency domains of the convolution. Convolving in one domain corresponds to elementwise multiplication in the other domain. The convolution theorem can be used to perform convolution via multiplication in the time domain.</p>

