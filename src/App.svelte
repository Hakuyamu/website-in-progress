<script>
	import { onMount } from 'svelte';

	let headline = '';
	let headlines = [
		"Nothing to see here yet.",
		"Hey, you clicked me.",
		"And again.",
		"Ur wasting ur time.",
		"Stop annoying me.",
		"Ouch! That hurts!",
		"For real. Stop it.",
		"Just. Stop. Clicking. Me.",
		"NOW!",
		"Aight, I'mma give up.",
		"'Never gonna give u up...'",
		"U just got rickrolled!",
		"Now, please vanish away.",
		"＞﹏＜",
		"Let's apply another strat.",
		"I beg you!! Leave me alone :(",
		"Do I mean nothing to u?",
		"U know what?",
		"I'm done with u."
	];
	let index = 0;
	let typing = false;

	onMount(async () => {
		typeWriter(headlines[index]);
		index += 1;
	});

	function typeWriter(content) {
		headline = '';
		let count = 0;

		typing = true;
		write();

		function write() {
			if (content.charAt(count) == '') {
				typing = false;
			} else {
				headline += content.charAt(count)
				count += 1;
				setTimeout(write, 120);
			}
		}
	}

	function switchHeadline() {
		if (index < headlines.length && typing === false) {
			typeWriter(headlines[index]);
			index += 1;
		}
	}

	function toggleLegalNotice() {
		let lnClasses = document.getElementById('legal-notice').classList;
		let ppClasses = document.getElementById('privacy-policy').classList;
		if (lnClasses.contains('shown')) {
			lnClasses.remove('shown');
		} else {
			lnClasses.add('shown');
			ppClasses.remove('shown');
		}
	}

	function togglePrivacyPolicy() {
		let lnClasses = document.getElementById('legal-notice').classList;
		let ppClasses = document.getElementById('privacy-policy').classList;
		if (ppClasses.contains('shown')) {
			ppClasses.remove('shown');
		} else {
			ppClasses.add('shown');
			lnClasses.remove('shown');
		}
	}
</script>

<section id="top-section">
	<div class="wrapper">
		<h1>{headline}</h1>
		<h2>Unless you just want to enjoy the pure emptiness, you might consider following me.</h2>
		<div class="button-container">
			<a href="https://github.com/Hakuyamu" id="github" target="_blank"><i class="fab fa-github"></i>GitHub</a
			><a href="https://www.instagram.com/heuerleon/" id="instagram" target="_blank"><i class="fab fa-instagram"></i>Instagram</a
			><a href="https://www.linkedin.com/in/leonheuer/" id="linkedin" target="_blank"><i class="fab fa-linkedin"></i>LinkedIn</a>
		</div>
	</div>
</section>

<span id="leonheuer" on:click={switchHeadline}>// Leon Heuer</span>
<div class="footer">
	<span on:click={toggleLegalNotice}>Legal Notice</span
	><span on:click={togglePrivacyPolicy}>Privacy Policy</span>
</div>

<div class="popup" id="legal-notice">
	<h1>Legal Notice<i class="fas fa-times" on:click={toggleLegalNotice}></i></h1>
	<div class="content">
		<h1>Impressum</h1>

		<h2>Angaben gem&auml;&szlig; &sect; 5 TMG</h2>
		<ul>
			<li>Leon Heuer</li>
			<li>Am Brahmberg 25</li>
			<li>23611 Bad Schwartau</li>
		</ul>

		<h2>Kontakt</h2>
		<ul>
			<li>Telefon: +49 176 66058083</li>
			<li>E-Mail: leon,heuer(at)outlook.de</li>
		</ul>

		<h1>Disclaimer</h1>

		<h2>Haftung für Inhalte</h2>
		<p>
			Als Diensteanbieter sind wir gemäß § 7 Abs.1 TMG für eigene Inhalte auf diesen Seiten nach den allgemeinen Gesetzen verantwortlich. Nach §§ 8 bis 10 TMG sind wir als Diensteanbieter jedoch nicht verpflichtet, übermittelte
			oder gespeicherte fremde Informationen zu überwachen oder nach Umständen zu forschen, die auf eine rechtswidrige Tätigkeit hinweisen.
		</p>
		<p>
			Verpflichtungen zur Entfernung oder Sperrung der Nutzung von Informationen nach den allgemeinen Gesetzen bleiben hiervon unberührt. Eine diesbezügliche Haftung ist jedoch erst ab dem Zeitpunkt der Kenntnis einer konkreten
			Rechtsverletzung möglich. Bei Bekanntwerden von entsprechenden Rechtsverletzungen werden wir diese Inhalte umgehend entfernen.
		</p>

		<h2>Haftung für Links</h2>
		<p>
			Unser Angebot enthält Links zu externen Websites Dritter, auf deren Inhalte wir keinen Einfluss haben. Deshalb können wir für diese fremden Inhalte auch keine Gewähr übernehmen. Für die Inhalte der verlinkten Seiten ist
			stets der jeweilige Anbieter oder Betreiber der Seiten verantwortlich. Die verlinkten Seiten wurden zum Zeitpunkt der Verlinkung auf mögliche Rechtsverstöße überprüft. Rechtswidrige Inhalte waren zum Zeitpunkt der
			Verlinkung nicht erkennbar.
		</p>
		<p>
			Eine permanente inhaltliche Kontrolle der verlinkten Seiten ist jedoch ohne konkrete Anhaltspunkte einer Rechtsverletzung nicht zumutbar. Bei Bekanntwerden von Rechtsverletzungen werden wir derartige Links umgehend entfernen.
		</p>

		<h2>Urheberrecht</h2>
		<p>
			Die durch die Seitenbetreiber erstellten Inhalte und Werke auf diesen Seiten unterliegen dem deutschen Urheberrecht. Die Vervielfältigung, Bearbeitung, Verbreitung und jede Art der Verwertung außerhalb der Grenzen des
			Urheberrechtes bedürfen der schriftlichen Zustimmung des jeweiligen Autors bzw. Erstellers. Downloads und Kopien dieser Seite sind nur für den privaten, nicht kommerziellen Gebrauch gestattet.
		</p>
		<p>
			Soweit die Inhalte auf dieser Seite nicht vom Betreiber erstellt wurden, werden die Urheberrechte Dritter beachtet. Insbesondere werden Inhalte Dritter als solche gekennzeichnet. Sollten Sie trotzdem auf eine
			Urheberrechtsverletzung aufmerksam werden, bitten wir um einen entsprechenden Hinweis. Bei Bekanntwerden von Rechtsverletzungen werden wir derartige Inhalte umgehend entfernen.
		</p>

		<p>
			Quelle: <a href="https://www.e-recht24.de">https://www.e-recht24.de</a>
		</p>
	</div>
</div>

<div class="popup" id="privacy-policy">
	<h1>Privacy Policy<i class="fas fa-times" on:click={togglePrivacyPolicy}></i></h1>
	<div class="content">
		<h1>Datenschutz&shy;erkl&auml;rung</h1>

		<h2>1. Datenschutz auf einen Blick</h2>

		<h3>Allgemeine Hinweise</h3>
		<p>
			Die folgenden Hinweise geben einen einfachen &Uuml;berblick dar&uuml;ber, was mit Ihren personenbezogenen Daten passiert, wenn Sie diese Website besuchen. Personenbezogene Daten sind alle Daten, mit denen Sie pers&ouml;nlich
			identifiziert werden k&ouml;nnen. Ausf&uuml;hrliche Informationen zum Thema Datenschutz entnehmen Sie unserer unter diesem Text aufgef&uuml;hrten Datenschutzerkl&auml;rung.
		</p>

		<h3>Datenerfassung auf dieser Website</h3>
		<h4>Wer ist verantwortlich f&uuml;r die Datenerfassung auf dieser Website?</h4>
		<p>
			Die Datenverarbeitung auf dieser Website erfolgt durch den Websitebetreiber. Dessen Kontaktdaten k&ouml;nnen Sie dem Abschnitt &bdquo;Hinweis zur Verantwortlichen Stelle&ldquo; in dieser Datenschutzerkl&auml;rung entnehmen.
		</p>
		<h4>Wie erfassen wir Ihre Daten?</h4>
		<p>
			Ihre Daten werden zum einen dadurch erhoben, dass Sie uns diese mitteilen. Hierbei kann es sich z.&nbsp;B. um Daten handeln, die Sie in ein Kontaktformular eingeben.
		</p>
		<p>
			Andere Daten werden automatisch oder nach Ihrer Einwilligung beim Besuch der Website durch unsere IT-Systeme erfasst. Das sind vor allem technische Daten (z.&nbsp;B. Internetbrowser, Betriebssystem oder Uhrzeit des
			Seitenaufrufs). Die Erfassung dieser Daten erfolgt automatisch, sobald Sie diese Website betreten.
		</p>
		<h4>Wof&uuml;r nutzen wir Ihre Daten?</h4>
		<p>
			Ein Teil der Daten wird erhoben, um eine fehlerfreie Bereitstellung der Website zu gew&auml;hrleisten. Andere Daten k&ouml;nnen zur Analyse Ihres Nutzerverhaltens verwendet werden.
		</p>
		<h4>Welche Rechte haben Sie bez&uuml;glich Ihrer Daten?</h4>
		<p>
			Sie haben jederzeit das Recht, unentgeltlich Auskunft &uuml;ber Herkunft, Empf&auml;nger und Zweck Ihrer gespeicherten personenbezogenen Daten zu erhalten. Sie haben au&szlig;erdem ein Recht, die Berichtigung oder
			L&ouml;schung dieser Daten zu verlangen. Wenn Sie eine Einwilligung zur Datenverarbeitung erteilt haben, k&ouml;nnen Sie diese Einwilligung jederzeit f&uuml;r die Zukunft widerrufen. Au&szlig;erdem haben Sie das Recht,
			unter bestimmten Umst&auml;nden die Einschr&auml;nkung der Verarbeitung Ihrer personenbezogenen Daten zu verlangen. Des Weiteren steht Ihnen ein Beschwerderecht bei der zust&auml;ndigen Aufsichtsbeh&ouml;rde zu.
		</p>
		<p>
			Hierzu sowie zu weiteren Fragen zum Thema Datenschutz k&ouml;nnen Sie sich jederzeit an uns wenden.
		</p>

		<h2>2. Hosting</h2>

		<h3>Externes Hosting</h3>
		<p>
			Diese Website wird bei einem externen Dienstleister gehostet (Hoster). Die personenbezogenen Daten, die auf dieser Website erfasst werden, werden auf den Servern des Hosters gespeichert. Hierbei kann es sich v. a.
			um IP-Adressen, Kontaktanfragen, Meta- und Kommunikationsdaten, Vertragsdaten, Kontaktdaten, Namen, Websitezugriffe und sonstige Daten, die &uuml;ber eine Website generiert werden, handeln.
		</p>
		<p>
			Der Einsatz des Hosters erfolgt zum Zwecke der Vertragserf&uuml;llung gegen&uuml;ber unseren potenziellen und bestehenden Kunden (Art. 6 Abs. 1 lit. b DSGVO) und im Interesse einer sicheren, schnellen und effizienten
			Bereitstellung unseres Online-Angebots durch einen professionellen Anbieter (Art. 6 Abs. 1 lit. f DSGVO).
		</p>
		<p>
			Unser Hoster wird Ihre Daten nur insoweit verarbeiten, wie dies zur Erf&uuml;llung seiner Leistungspflichten erforderlich ist und unsere Weisungen in Bezug auf diese Daten befolgen.
		</p>

		<p>Wir setzen folgenden Hoster ein:</p>
		<ul>
			<li>myLoc managed IT AG</li>
			<li>Am Gatherhof 44</li>
			<li>40472 D&uuml;sseldorf</li>
			<li>Deutschland</li>
		</ul>

		<h2>3. Allgemeine Hinweise und Pflicht&shy;informationen</h2>

		<h3>Datenschutz</h3>
		<p>
			Die Betreiber dieser Seiten nehmen den Schutz Ihrer pers&ouml;nlichen Daten sehr ernst. Wir behandeln Ihre personenbezogenen Daten vertraulich und entsprechend den gesetzlichen Datenschutzvorschriften sowie dieser
			Datenschutzerkl&auml;rung.
		</p>
		<p>
			Wenn Sie diese Website benutzen, werden verschiedene personenbezogene Daten erhoben. Personenbezogene Daten sind Daten, mit denen Sie pers&ouml;nlich identifiziert werden k&ouml;nnen. Die vorliegende Datenschutzerkl&auml;rung
			erl&auml;utert, welche Daten wir erheben und wof&uuml;r wir sie nutzen. Sie erl&auml;utert auch, wie und zu welchem Zweck das geschieht.
		</p>
		<p>
			Wir weisen darauf hin, dass die Daten&uuml;bertragung im Internet (z.&nbsp;B. bei der Kommunikation per E-Mail) Sicherheitsl&uuml;cken aufweisen kann. Ein l&uuml;ckenloser Schutz der Daten vor dem Zugriff durch
			Dritte ist nicht m&ouml;glich.
		</p>

		<h3>Hinweis zur verantwortlichen Stelle</h3>
		<p>Die verantwortliche Stelle f&uuml;r die Datenverarbeitung auf dieser Website ist:</p>
		<ul>
			<li>Leon Heuer</li>
			<li>Am Brahmberg 25</li>
			<li>23611 Bad Schwartau</li>
			<li>Telefon: +49 176 66058083</li>
			<li>E-Mail: leon,heuer(at)outlook.de</li>
		</ul>
		<p>
			Verantwortliche Stelle ist die nat&uuml;rliche oder juristische Person, die allein oder gemeinsam mit anderen &uuml;ber die Zwecke und Mittel der Verarbeitung von personenbezogenen Daten (z.&nbsp;B. Namen, E-Mail-Adressen
			o. &Auml;.) entscheidet.
		</p>

		<h3>Speicherdauer</h3>
		<p>
			Soweit innerhalb dieser Datenschutzerkl&auml;rung keine speziellere Speicherdauer genannt wurde, verbleiben Ihre personenbezogenen Daten bei uns, bis der Zweck f&uuml;r die Datenverarbeitung entf&auml;llt. Wenn Sie
			ein berechtigtes L&ouml;schersuchen geltend machen oder eine Einwilligung zur Datenverarbeitung widerrufen, werden Ihre Daten gel&ouml;scht, sofern wir keine anderen rechtlich zul&auml;ssigen Gr&uuml;nde f&uuml;r die
			Speicherung Ihrer personenbezogenen Daten haben (z.&nbsp;B. steuer- oder handelsrechtliche Aufbewahrungsfristen); im letztgenannten Fall erfolgt die L&ouml;schung nach Fortfall dieser Gr&uuml;nde.
		</p>

		<h3>Hinweis zur Datenweitergabe in die USA und sonstige Drittstaaten</h3>
		<p>
			Wir verwenden unter anderem Tools von Unternehmen mit Sitz in den USA oder sonstigen datenschutzrechtlich nicht sicheren Drittstaaten. Wenn diese Tools aktiv sind, k&ouml;nnen Ihre personenbezogene Daten in diese Drittstaaten
			&uuml;bertragen und dort verarbeitet werden. Wir weisen darauf hin, dass in diesen L&auml;ndern kein mit der EU vergleichbares Datenschutzniveau garantiert werden kann. Beispielsweise sind US-Unternehmen dazu verpflichtet,
			personenbezogene Daten an Sicherheitsbeh&ouml;rden herauszugeben, ohne dass Sie als Betroffener hiergegen gerichtlich vorgehen k&ouml;nnten. Es kann daher nicht ausgeschlossen werden, dass US-Beh&ouml;rden (z.&nbsp;B.
			Geheimdienste) Ihre auf US-Servern befindlichen Daten zu &Uuml;berwachungszwecken verarbeiten, auswerten und dauerhaft speichern. Wir haben auf diese Verarbeitungst&auml;tigkeiten keinen Einfluss.
		</p>
		
		<h3>Widerruf Ihrer Einwilligung zur Datenverarbeitung</h3>
		<p>
			Viele Datenverarbeitungsvorg&auml;nge sind nur mit Ihrer ausdr&uuml;cklichen Einwilligung m&ouml;glich. Sie k&ouml;nnen eine bereits erteilte Einwilligung jederzeit widerrufen. Die Rechtm&auml;&szlig;igkeit der bis zum
			Widerruf erfolgten Datenverarbeitung bleibt vom Widerruf unber&uuml;hrt.
		</p>

		<h3>Widerspruchsrecht gegen die Datenerhebung in besonderen F&auml;llen sowie gegen Direktwerbung (Art. 21 DSGVO)</h3>
		<p>
			WENN DIE DATENVERARBEITUNG AUF GRUNDLAGE VON ART. 6 ABS. 1 LIT. E ODER F DSGVO ERFOLGT, HABEN SIE JEDERZEIT DAS RECHT, AUS GR&Uuml;NDEN, DIE SICH AUS IHRER BESONDEREN SITUATION ERGEBEN, GEGEN DIE VERARBEITUNG IHRER
			PERSONENBEZOGENEN DATEN WIDERSPRUCH EINZULEGEN; DIES GILT AUCH F&Uuml;R EIN AUF DIESE BESTIMMUNGEN GEST&Uuml;TZTES PROFILING. DIE JEWEILIGE RECHTSGRUNDLAGE, AUF DENEN EINE VERARBEITUNG BERUHT, ENTNEHMEN SIE DIESER
			DATENSCHUTZERKL&Auml;RUNG. WENN SIE WIDERSPRUCH EINLEGEN, WERDEN WIR IHRE BETROFFENEN PERSONENBEZOGENEN DATEN NICHT MEHR VERARBEITEN, ES SEI DENN, WIR K&Ouml;NNEN ZWINGENDE SCHUTZW&Uuml;RDIGE GR&Uuml;NDE F&Uuml;R DIE
			VERARBEITUNG NACHWEISEN, DIE IHRE INTERESSEN, RECHTE UND FREIHEITEN &Uuml;BERWIEGEN ODER DIE VERARBEITUNG DIENT DER GELTENDMACHUNG, AUS&Uuml;BUNG ODER VERTEIDIGUNG VON RECHTSANSPR&Uuml;CHEN (WIDERSPRUCH NACH ART. 21 ABS. 1 DSGVO).
		</p>
		<p>
			WERDEN IHRE PERSONENBEZOGENEN DATEN VERARBEITET, UM DIREKTWERBUNG ZU BETREIBEN, SO HABEN SIE DAS RECHT, JEDERZEIT WIDERSPRUCH GEGEN DIE VERARBEITUNG SIE BETREFFENDER PERSONENBEZOGENER DATEN ZUM ZWECKE DERARTIGER WERBUNG
			EINZULEGEN; DIES GILT AUCH F&Uuml;R DAS PROFILING, SOWEIT ES MIT SOLCHER DIREKTWERBUNG IN VERBINDUNG STEHT. WENN SIE WIDERSPRECHEN, WERDEN IHRE PERSONENBEZOGENEN DATEN ANSCHLIESSEND NICHT MEHR ZUM ZWECKE DER DIREKTWERBUNG
			VERWENDET (WIDERSPRUCH NACH ART. 21 ABS. 2 DSGVO).
		</p>

		<h3>Beschwerde&shy;recht bei der zust&auml;ndigen Aufsichts&shy;beh&ouml;rde</h3>
		<p>
			Im Falle von Verst&ouml;&szlig;en gegen die DSGVO steht den Betroffenen ein Beschwerderecht bei einer Aufsichtsbeh&ouml;rde, insbesondere in dem Mitgliedstaat ihres gew&ouml;hnlichen Aufenthalts, ihres Arbeitsplatzes
			oder des Orts des mutma&szlig;lichen Versto&szlig;es zu. Das Beschwerderecht besteht unbeschadet anderweitiger verwaltungsrechtlicher oder gerichtlicher Rechtsbehelfe.
		</p>

		<h3>Recht auf Daten&shy;&uuml;bertrag&shy;barkeit</h3>
		<p>
			Sie haben das Recht, Daten, die wir auf Grundlage Ihrer Einwilligung oder in Erf&uuml;llung eines Vertrags automatisiert verarbeiten, an sich oder an einen Dritten in einem g&auml;ngigen, maschinenlesbaren Format
			aush&auml;ndigen zu lassen. Sofern Sie die direkte &Uuml;bertragung der Daten an einen anderen Verantwortlichen verlangen, erfolgt dies nur, soweit es technisch machbar ist.
		</p>

		<h3>SSL- bzw. TLS-Verschl&uuml;sselung</h3>
		<p>
			Diese Seite nutzt aus Sicherheitsgr&uuml;nden und zum Schutz der &Uuml;bertragung vertraulicher Inhalte, wie zum Beispiel Bestellungen oder Anfragen, die Sie an uns als Seitenbetreiber senden, eine SSL- bzw.
			TLS-Verschl&uuml;sselung. Eine verschl&uuml;sselte Verbindung erkennen Sie daran, dass die Adresszeile des Browsers von &bdquo;http://&ldquo; auf &bdquo;https://&ldquo; wechselt und an dem Schloss-Symbol in Ihrer Browserzeile.
		</p>
		<p>
			Wenn die SSL- bzw. TLS-Verschl&uuml;sselung aktiviert ist, k&ouml;nnen die Daten, die Sie an uns &uuml;bermitteln, nicht von Dritten mitgelesen werden.
		</p>

		<h3>Auskunft, L&ouml;schung und Berichtigung</h3>
		<p>
			Sie haben im Rahmen der geltenden gesetzlichen Bestimmungen jederzeit das Recht auf unentgeltliche Auskunft &uuml;ber Ihre gespeicherten personenbezogenen Daten, deren Herkunft und Empf&auml;nger und den Zweck der
			Datenverarbeitung und ggf. ein Recht auf Berichtigung oder L&ouml;schung dieser Daten. Hierzu sowie zu weiteren Fragen zum Thema personenbezogene Daten k&ouml;nnen Sie sich jederzeit an uns wenden.
		</p>

		<h3>Recht auf Einschr&auml;nkung der Verarbeitung</h3>
		<p>
			Sie haben das Recht, die Einschr&auml;nkung der Verarbeitung Ihrer personenbezogenen Daten zu verlangen. Hierzu k&ouml;nnen Sie sich jederzeit an uns wenden. Das Recht auf Einschr&auml;nkung der Verarbeitung besteht in
			folgenden F&auml;llen:
		</p>
		<ul>
			<li>
				Wenn Sie die Richtigkeit Ihrer bei uns gespeicherten personenbezogenen Daten bestreiten, ben&ouml;tigen wir in der Regel Zeit, um dies zu &uuml;berpr&uuml;fen. F&uuml;r die Dauer der Pr&uuml;fung haben Sie das Recht,
				die Einschr&auml;nkung der Verarbeitung Ihrer personenbezogenen Daten zu verlangen.
			</li>
			<li>
				Wenn die Verarbeitung Ihrer personenbezogenen Daten unrechtm&auml;&szlig;ig geschah/geschieht, k&ouml;nnen Sie statt der L&ouml;schung die Einschr&auml;nkung der Datenverarbeitung verlangen.
			</li>
			<li>
				Wenn wir Ihre personenbezogenen Daten nicht mehr ben&ouml;tigen, Sie sie jedoch zur Aus&uuml;bung, Verteidigung oder Geltendmachung von Rechtsanspr&uuml;chen ben&ouml;tigen, haben Sie das Recht, statt der L&ouml;schung die
				Einschr&auml;nkung der Verarbeitung Ihrer personenbezogenen Daten zu verlangen.
			</li>
			<li>
				Wenn Sie einen Widerspruch nach Art. 21 Abs. 1 DSGVO eingelegt haben, muss eine Abw&auml;gung zwischen Ihren und unseren Interessen vorgenommen werden. Solange noch nicht feststeht, wessen Interessen &uuml;berwiegen,
				haben Sie das Recht, die Einschr&auml;nkung der Verarbeitung Ihrer personenbezogenen Daten zu verlangen.
			</li>
		</ul>
		<p>
			Wenn Sie die Verarbeitung Ihrer personenbezogenen Daten eingeschr&auml;nkt haben, d&uuml;rfen diese Daten &ndash; von ihrer Speicherung abgesehen &ndash; nur mit Ihrer Einwilligung oder zur Geltendmachung, Aus&uuml;bung
			oder Verteidigung von Rechtsanspr&uuml;chen oder zum Schutz der Rechte einer anderen nat&uuml;rlichen oder juristischen Person oder aus Gr&uuml;nden eines wichtigen &ouml;ffentlichen Interesses der Europ&auml;ischen Union
			oder eines Mitgliedstaats verarbeitet werden.
		</p>
		
		<h2>4. Datenerfassung auf dieser Website</h2>

		<h3>Anfrage per E-Mail, Telefon oder Telefax</h3>
		<p>
			Wenn Sie uns per E-Mail, Telefon oder Telefax kontaktieren, wird Ihre Anfrage inklusive aller daraus hervorgehenden personenbezogenen Daten (Name, Anfrage) zum Zwecke der Bearbeitung Ihres Anliegens bei uns gespeichert und
			verarbeitet. Diese Daten geben wir nicht ohne Ihre Einwilligung weiter.
		</p>
		<p>
			Die Verarbeitung dieser Daten erfolgt auf Grundlage von Art. 6 Abs. 1 lit. b DSGVO, sofern Ihre Anfrage mit der Erf&uuml;llung eines Vertrags zusammenh&auml;ngt oder zur Durchf&uuml;hrung vorvertraglicher Ma&szlig;nahmen
			erforderlich ist. In allen &uuml;brigen F&auml;llen beruht die Verarbeitung auf unserem berechtigten Interesse an der effektiven Bearbeitung der an uns gerichteten Anfragen (Art. 6 Abs. 1 lit. f DSGVO) oder auf Ihrer
			Einwilligung (Art. 6 Abs. 1 lit. a DSGVO) sofern diese abgefragt wurde.
		</p>
		<p>
			Die von Ihnen an uns per Kontaktanfragen &uuml;bersandten Daten verbleiben bei uns, bis Sie uns zur L&ouml;schung auffordern, Ihre Einwilligung zur Speicherung widerrufen oder der Zweck f&uuml;r die Datenspeicherung
			entf&auml;llt (z.&nbsp;B. nach abgeschlossener Bearbeitung Ihres Anliegens). Zwingende gesetzliche Bestimmungen &ndash; insbesondere gesetzliche Aufbewahrungsfristen &ndash; bleiben unber&uuml;hrt.
		</p>

		<h2>5. Plugins und Tools</h2>
		
		<h3>Google Web Fonts (lokales Hosting)</h3>
		<p>
			Diese Seite nutzt zur einheitlichen Darstellung von Schriftarten so genannte Web Fonts, die von Google bereitgestellt werden. Die Google Fonts sind lokal installiert. Eine Verbindung zu Servern von Google findet
			dabei nicht statt.
		</p>
		<p>
			Weitere Informationen zu Google Web Fonts finden Sie unter <a href="https://developers.google.com/fonts/faq" target="_blank" rel="noopener noreferrer">https://developers.google.com/fonts/faq</a> und in der
			Datenschutzerkl&auml;rung von Google: <a href="https://policies.google.com/privacy?hl=de" target="_blank" rel="noopener noreferrer">https://policies.google.com/privacy?hl=de</a>.
		</p>

		<h3>Font Awesome</h3>
		<p>
			Diese Seite nutzt zur einheitlichen Darstellung von Schriftarten und Symbolen Font Awesome. Anbieter ist die Fonticons, Inc., 6 Porter Road Apartment 3R, Cambridge, Massachusetts, USA.
		</p>
		<p>
			Beim Aufruf einer Seite l&auml;dt Ihr Browser die ben&ouml;tigten Fonts in ihren Browsercache, um Texte, Schriftarten und Symbole korrekt anzuzeigen. Zu diesem Zweck muss der von Ihnen verwendete Browser Verbindung
			zu den Servern von Font Awesome aufnehmen. Hierdurch erlangt Font Awesome Kenntnis dar&uuml;ber, dass &uuml;ber Ihre IP-Adresse diese Website aufgerufen wurde. Die Nutzung von Font Awesome erfolgt auf Grundlage
			von Art. 6 Abs. 1 lit. f DSGVO. Wir haben ein berechtigtes Interesse an der einheitlichen Darstellung des Schriftbildes auf unserer Website. Sofern eine entsprechende Einwilligung abgefragt wurde (z.&nbsp;B. eine
			Einwilligung zur Speicherung von Cookies), erfolgt die Verarbeitung ausschlie&szlig;lich auf Grundlage von Art. 6 Abs. 1 lit. a DSGVO; die Einwilligung ist jederzeit widerrufbar.
		</p>
		<p>
			Wenn Ihr Browser Font Awesome nicht unterst&uuml;tzt, wird eine Standardschrift von Ihrem Computer genutzt.
		</p>
		<p>
			Weitere Informationen zu Font Awesome finden Sie&nbsp;und in der Datenschutzerkl&auml;rung von Font Awesome unter:
			<a href="https://fontawesome.com/privacy" target="_blank" rel="noopener noreferrer">https://fontawesome.com/privacy</a>.
		</p>
		<p>
			Quelle: <a href="https://www.e-recht24.de">https://www.e-recht24.de</a>
		</p>
	</div>
</div>
