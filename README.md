# Ontologies

Ontology for public transportation domain modeled in Prot�g� <http://protege.stanford.edu/>.
transportationJourneyPlanner.owl

Mapped classes:

	Passageiro
		Adulto
		Idoso
	Rota
		Cal�ada
		CorredorDeOnibus
		Rua
	Terminal
		PontoDeLota��o
		PontoDeOnibus
		PontoDeTaxi
	TransportePublico
		Bicicleta
		Lota��o	
		Onibus
		Taxi

Data properties:
	
	documentosEst�oVencidos
	temLugarDisponivel
	�PassageiroPreferencial

Object properties:

	podeAndarDe
	podePararEm
	podeSerMultado
	seLocomoveEm

Rules:

	TransportePublico(?t), temLugarDisponivel(?t, true), Passageiro(?p) -> podeAndarDe(?p, ?t)
	Onibus(?o), PontoDeOnibus(?p) -> podePararEm(?o, ?p)
	TransportePublico(?p), documentosEst�oVencidos(?p, true) -> podeSerMultado(?p, ?p)
	Lota��o(?l), PontoDeLota��o(?p) -> podePararEm(?l, ?p)
	Onibus(?b), CorredorDeOnibus(?c) -> seLocomoveEm(?b, ?c)
	Idoso(?i), Onibus(?o), temLugarDisponivel(?o, false), �PassageiroPreferencial(?i, true) -> podeAndarDe(?i, ?o)
	Taxi(?t), PontoDeTaxi(?p) -> podePararEm(?t, ?p)
	Adulto(?a), Bicicleta(?b) -> podeAndarDe(?a, ?b)
	Passageiro(?p), Onibus(?o), temLugarDisponivel(?o, true) -> podeAndarDe(?p, ?o)
	Bicicleta(?h), Cal�ada(?y) -> seLocomoveEm(?h, ?y)