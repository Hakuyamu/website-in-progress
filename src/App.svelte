<script>
	import { onMount } from 'svelte';

	let headline = '';
	let headlines = [
		'Nothing to see here yet.',
		'Hey, you clicked me.',
		'And again.',
		'Ur wasting ur time.',
		'Stop annoying me.',
		'Ouch! That hurts!',
		'For real. Stop it.',
		'Just. Stop. Clicking. Me.',
		'NOW!',
		'Aight, imma give up.',
		'"Never gonna give u up..."',
		'U just got rickrolled!',
		'Now, please vanish away.',
		'＞﹏＜',
		'Lets apply another strat.',
		'I beg you!! Leave me alone :(',
		'Do I mean nothing to u?',
		'U know what?',
		'Im done with u.'
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
		<p>Impressum</p>
		<p>Angaben gemäß § 5 Telemediengesetz</p>

		<p>Allgemeine Informationen</p>

		<p>Name und Anschrift</p>
		<ul>
			<li>Michael Mitteldorf</li>
			<li>Zur Höhe 15a</li>
			<li>Deutschland</li>
		</ul>
		
		<p>E-Mail-Adresse: caveclown@web.de</p>
		<p>Telefon 0177 5883862</p>
		<p>Umsatzsteuer-ID Umsatzsteuer-Identifikationsnummer gemäß §27 a Umsatzsteuergesetz wird aufgrund der Kleinunternehmer-Regelung nach §19 UStG nicht ausgewiesen.</p>

		<p>Weitere Informationen</p>

		<p>Haftung für Inhalte</p>
		<p>
			Als Diensteanbieter sind wir gemäß § 7 Abs.1 TMG für eigene Inhalte auf diesen Seiten nach den allgemeinen Gesetzen verantwortlich. Nach §§ 8 bis 10 TMG sind wir als Diensteanbieter jedoch nicht verpflichtet,
			übermittelte oder gespeicherte fremde Informationen zu überwachen oder nach Umständen zu forschen, die auf eine rechtswidrige Tätigkeit hinweisen.
		</p>
		<p>
			Verpflichtungen zur Entfernung oder Sperrung der Nutzung von Informationen nach den allgemeinen Gesetzen bleiben hiervon unberührt. Eine diesbezügliche Haftung ist jedoch erst ab dem Zeitpunkt der Kenntnis einer
			konkreten Rechtsverletzung möglich. Bei Bekanntwerden von entsprechenden Rechtsverletzungen werden wir diese Inhalte umgehend entfernen.
		</p>
				
		<p>Haftung für Links</p>
		<p>
			Unser Angebot enthält Links zu externen Websites Dritter, auf deren Inhalte wir keinen Einfluss haben. Deshalb können wir für diese fremden Inhalte auch keine Gewähr übernehmen. Für die Inhalte der verlinkten
			Seiten ist stets der jeweilige Anbieter oder Betreiber der Seiten verantwortlich. Die verlinkten Seiten wurden zum Zeitpunkt der Verlinkung auf mögliche Rechtsverstöße überprüft. Rechtswidrige Inhalte waren zum
			Zeitpunkt der Verlinkung nicht erkennbar.
		</p>
		<p>
			Eine permanente inhaltliche Kontrolle der verlinkten Seiten ist jedoch ohne konkrete Anhaltspunkte einer Rechtsverletzung nicht zumutbar. Bei Bekanntwerden von Rechtsverletzungen werden wir derartige Links umgehend entfernen.
		</p>		

		<p>Urheberrecht</p>
		<p>
			Die durch die Seitenbetreiber erstellten Inhalte und Werke auf diesen Seiten unterliegen dem deutschen Urheberrecht. Die Vervielfältigung, Bearbeitung, Verbreitung und jede Art der Verwertung außerhalb der Grenzen des
			Urheberrechtes bedürfen der schriftlichen Zustimmung des jeweiligen Autors bzw. Erstellers. Downloads und Kopien dieser Seite sind nur für den privaten, nicht kommerziellen Gebrauch gestattet.
		</p>
		<p>
			Soweit die Inhalte auf dieser Seite nicht vom Betreiber erstellt wurden, werden die Urheberrechte Dritter beachtet. Insbesondere werden Inhalte Dritter als solche gekennzeichnet. Sollten Sie trotzdem auf eine
			Urheberrechtsverletzung aufmerksam werden, bitten wir um einen entsprechenden Hinweis. Bei Bekanntwerden von Rechtsverletzungen werden wir derartige Inhalte umgehend entfernen.
		</p>
	</div>
</div>

<div class="popup" id="privacy-policy">
	<h1>Privacy Policy<i class="fas fa-times" on:click={togglePrivacyPolicy}></i></h1>
	<div class="content">
		<p>Impressum</p>
		<p>Angaben gemäß § 5 Telemediengesetz</p>

		<p>Allgemeine Informationen</p>

		<p>Name und Anschrift</p>
		<ul>
			<li>Michael Mitteldorf</li>
			<li>Zur Höhe 15a</li>
			<li>Deutschland</li>
		</ul>
		
		<p>E-Mail-Adresse: caveclown@web.de</p>
		<p>Telefon 0177 5883862</p>
		<p>Umsatzsteuer-ID Umsatzsteuer-Identifikationsnummer gemäß §27 a Umsatzsteuergesetz wird aufgrund der Kleinunternehmer-Regelung nach §19 UStG nicht ausgewiesen.</p>

		<p>Weitere Informationen</p>

		<p>Haftung für Inhalte</p>
		<p>
			Als Diensteanbieter sind wir gemäß § 7 Abs.1 TMG für eigene Inhalte auf diesen Seiten nach den allgemeinen Gesetzen verantwortlich. Nach §§ 8 bis 10 TMG sind wir als Diensteanbieter jedoch nicht verpflichtet,
			übermittelte oder gespeicherte fremde Informationen zu überwachen oder nach Umständen zu forschen, die auf eine rechtswidrige Tätigkeit hinweisen.
		</p>
		<p>
			Verpflichtungen zur Entfernung oder Sperrung der Nutzung von Informationen nach den allgemeinen Gesetzen bleiben hiervon unberührt. Eine diesbezügliche Haftung ist jedoch erst ab dem Zeitpunkt der Kenntnis einer
			konkreten Rechtsverletzung möglich. Bei Bekanntwerden von entsprechenden Rechtsverletzungen werden wir diese Inhalte umgehend entfernen.
		</p>
				
		<p>Haftung für Links</p>
		<p>
			Unser Angebot enthält Links zu externen Websites Dritter, auf deren Inhalte wir keinen Einfluss haben. Deshalb können wir für diese fremden Inhalte auch keine Gewähr übernehmen. Für die Inhalte der verlinkten
			Seiten ist stets der jeweilige Anbieter oder Betreiber der Seiten verantwortlich. Die verlinkten Seiten wurden zum Zeitpunkt der Verlinkung auf mögliche Rechtsverstöße überprüft. Rechtswidrige Inhalte waren zum
			Zeitpunkt der Verlinkung nicht erkennbar.
		</p>
		<p>
			Eine permanente inhaltliche Kontrolle der verlinkten Seiten ist jedoch ohne konkrete Anhaltspunkte einer Rechtsverletzung nicht zumutbar. Bei Bekanntwerden von Rechtsverletzungen werden wir derartige Links umgehend entfernen.
		</p>		

		<p>Urheberrecht</p>
		<p>
			Die durch die Seitenbetreiber erstellten Inhalte und Werke auf diesen Seiten unterliegen dem deutschen Urheberrecht. Die Vervielfältigung, Bearbeitung, Verbreitung und jede Art der Verwertung außerhalb der Grenzen des
			Urheberrechtes bedürfen der schriftlichen Zustimmung des jeweiligen Autors bzw. Erstellers. Downloads und Kopien dieser Seite sind nur für den privaten, nicht kommerziellen Gebrauch gestattet.
		</p>
		<p>
			Soweit die Inhalte auf dieser Seite nicht vom Betreiber erstellt wurden, werden die Urheberrechte Dritter beachtet. Insbesondere werden Inhalte Dritter als solche gekennzeichnet. Sollten Sie trotzdem auf eine
			Urheberrechtsverletzung aufmerksam werden, bitten wir um einen entsprechenden Hinweis. Bei Bekanntwerden von Rechtsverletzungen werden wir derartige Inhalte umgehend entfernen.
		</p>
	</div>
</div>
