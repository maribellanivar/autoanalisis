import { useState, useEffect } from "react";

const Q = [
  { id:1,  b:"Miedo al Fracaso",       t:"Cuando sientes que Dios te llama a algo grande, ¿cuál es tu reacción más honesta?",                              s:"Elige la que más se parece a lo que realmente pasa dentro de ti.",                                       o:["Me emociono y actúo aunque no vea todo el camino","Me emociono, pero llega el '¿y si fallo?' y me paralizo","Dudo si realmente lo escuché bien — quizás no es para mí","Lo proceso durante meses sin tomar ninguna acción"] },
  { id:2,  b:"Autoestima",             t:"Cuando alguien te hace un cumplido genuino sobre algo que lograste, ¿qué haces?",                                s:"La forma en que recibes el reconocimiento revela cuánto crees en tu propio valor.",                      o:["Lo recibo con gratitud — sé que trabajé duro para eso","Lo minimizo: 'no es para tanto', 'fue suerte'","Me incomoda — aceptarlo me hace parecer arrogante","Lo necesito para sentirme bien — sin ese reconocimiento dudo de mí misma"] },
  { id:3,  b:"Aprobación Externa",     t:"Cuando tomas una decisión importante, ¿qué necesitas antes de actuar?",                                           s:"Piensa en la última decisión grande que tomaste o que estás considerando.",                               o:["Oración y claridad interna — confío en lo que Dios me dice","La opinión de alguien que admiro — sin eso me siento insegura","Que la mayoría de mi círculo esté de acuerdo","Certeza total — necesito saber que va a salir bien antes de moverme"] },
  { id:4,  b:"Comparación",            t:"Cuando ves a otra mujer triunfar en algo que tú también quieres, ¿qué sientes honestamente?",                    s:"No la respuesta espiritual — la primera reacción real.",                                                 o:["Genuina alegría — si ella pudo, yo también puedo","Inspiración mezclada con una punzada de '¿por qué ella y no yo?'","Comparo mis logros con los suyos y siempre salgo perdiendo","Me desanimo — siento que ya no hay espacio para mí"] },
  { id:5,  b:"Autosabotaje",           t:"¿Cuántas veces has estado a punto de dar un paso importante y algo 'surgió' para impedirlo?",                    s:"Ese 'algo' a veces viene de afuera. Y a veces lo creamos nosotras mismas sin darnos cuenta.",            o:["Rara vez — cuando me propongo algo lo hago aunque sea difícil","A veces — hay circunstancias que complican las cosas","Con frecuencia — justo cuando iba a empezar, algo me detiene","Casi siempre — llevo años llegando hasta la puerta sin entrar"] },
  { id:6,  b:"Mentalidad",             t:"Cuando algo no te sale como esperabas, ¿cuál es tu voz interior?",                                               s:"La forma en que te hablas cuando las cosas fallan revela tu mentalidad base.",                            o:["'Esto me enseña algo — ¿qué necesito ajustar?'","'Debí esperar más — no estaba lista todavía'","'Siempre me pasa lo mismo — no sé por qué sigo intentando'","'Sabía que iba a fallar — no estoy hecha para esto'"] },
  { id:7,  b:"Perfeccionismo",         t:"¿Cuánto tiempo llevas esperando el 'momento perfecto' para empezar algo que ya sabes que debes hacer?",          s:"El perfeccionismo rara vez se llama a sí mismo por su nombre. Se disfraza de responsabilidad.",          o:["No espero — empiezo imperfecta y lo refino en el camino","Unos meses — quiero más preparación antes de lanzarme","Más de un año — hay cosas que necesito resolver primero","Años — nunca siento que estoy completamente lista"] },
  { id:8,  b:"Disciplina",             t:"Cuando se trata de trabajar en tu propósito, ¿qué describe mejor lo que realmente pasa?",                        s:"No lo que quisieras que pasara — lo que realmente pasa.",                                                o:["Tengo rutinas consistentes — trabajo aunque no sienta motivación","Trabajo cuando me siento inspirada — si no, cuesta mucho empezar","Empiezo con energía y a las pocas semanas pierdo el ritmo","Me es difícil mantener cualquier compromiso conmigo misma"] },
  { id:9,  b:"Toma de Decisiones",     t:"Frente a una decisión importante que solo te afecta a ti, ¿cómo suele ser tu proceso?",                          s:"La forma en que decides revela si confías en la voz de Dios dentro de ti.",                              o:["Oro, evalúo, y decido — confío en lo que Dios me muestra","Busco la opinión de varias personas antes de decidir","Me cuesta mucho decidir — siempre siento que me puedo equivocar","Pospongo las decisiones importantes el mayor tiempo posible"] },
  { id:10, b:"Victimismo",             t:"Cuando piensas en por qué no has avanzado en tu propósito, ¿qué aparece primero?",                               s:"La honestidad en esta pregunta puede cambiar todo lo que viene después.",                                o:["Decisiones que yo misma tomé o evité — me hago responsable","El tiempo — si tuviera más tiempo todo sería diferente","Las circunstancias — mi situación no me lo permite ahora","Las personas — alguien en mi vida me lo ha impedido"] },
  { id:11, b:"Soltar el Control",      t:"Cuando Dios te pide que avances sin ver el camino completo, ¿qué pasa dentro de ti?",                            s:"La fe y el control no pueden ocupar el mismo espacio al mismo tiempo.",                                  o:["Lo doy — entiendo que el control es una ilusión y confío en Él","Lo intento soltar pero necesito tener al menos un plan B","Me cuesta muchísimo — la incertidumbre me genera ansiedad real","No puedo — prefiero quedarme donde estoy que arriesgarme"] },
  { id:12, b:"Críticas",               t:"Cuando alguien critica algo que hiciste con esfuerzo, ¿cuánto tiempo te afecta esa crítica?",                    s:"No lo que debería pasar — lo que realmente pasa en ti.",                                                 o:["La proceso, tomo lo que sirve, y sigo — no me detiene","Me afecta ese día pero al siguiente ya lo superé","Me quedo pensando días — sus palabras duermen en mi cabeza","Me paraliza — el miedo a ser criticada me hace no mostrar lo que hago"] },
  { id:13, b:"Inteligencia Emocional", t:"Cuando sientes emociones fuertes como ansiedad o miedo, ¿qué haces con ellas?",                                 s:"La forma en que manejas tus emociones determina si tú las usas o ellas te usan a ti.",                  o:["Las identifico, proceso, y uso como información — no me gobiernan","Las llevo a Dios en oración y eso generalmente me ayuda","Las evito o las entierro — prefiero seguir ocupada a sentirlas","Me dominan — cuando llegan, toman el control de mis decisiones"] },
  { id:14, b:"Perseverancia",          t:"Cuando algo que estás construyendo tarda más de lo esperado en dar frutos, ¿qué sueles hacer?",                  s:"El propósito siempre tarda más de lo que el ego espera.",                                                o:["Persisto — sé que los tiempos de Dios no son los míos","Me frustro pero sigo — aunque cueste más de lo que esperaba","Empiezo a dudar si realmente era un llamado de Dios","Lo abandono y busco otra cosa — necesito ver resultados pronto"] },
  { id:15, b:"Proximidad",             t:"Cuando piensas en las personas más cercanas a ti, ¿cómo describirías su influencia en tu camino hacia el propósito?", s:"El entorno más cercano puede impulsarte hacia quien Dios te llamó a ser — o puede ser tu barrera más silenciosa.", o:["Me rodeo de personas que me impulsan y creen en lo que Dios puso en mí","Algunas personas cercanas me apoyan pero otras generan dudas en mí","Las personas más cercanas a mí no entienden mi llamado y eso me frena","Mi entorno inmediato activamente me desanima o me hace sentir que no puedo"] }
];

const INFO = {
  "Miedo al Fracaso":       { d:"El miedo al fracaso no es cobardía — es la señal de que lo que Dios puso en ti importa demasiado. Pero cuando toma el control, cada día que no actúas es un día que la persona que necesitaba lo que tú tienes no lo recibió.", v:"«Porque no nos ha dado Dios espíritu de cobardía, sino de poder, de amor y de dominio propio.» — 2 Timoteo 1:7", a:"La raíz del miedo al fracaso no es el fracaso mismo — es lo que crees que el fracaso dice de ti. Ese es el trabajo de identidad." },
  "Autoestima":             { d:"La autoestima no se construye con afirmaciones. Se construye cuando tienes una identidad anclada en lo que Dios dice de ti — no en lo que produces ni en lo que los demás piensan. Una mujer que no cree en su propio valor no puede recibir el propósito que Dios diseñó para ella.", v:"«Porque somos hechura suya, creados en Cristo Jesús para buenas obras.» — Efesios 2:10", a:"Identificar de dónde viene tu sentido de valor ahora mismo — y redirigirlo hacia su única fuente real." },
  "Aprobación Externa":     { d:"Necesitar aprobación para avanzar es entregar tu propósito en manos de personas que no fueron diseñadas para cargarlo. Cada vez que esperas el permiso de alguien más, le estás diciendo a Dios que su voz no es suficiente.", v:"«Mas yo en Dios he confiado; no temeré lo que me pueda hacer el hombre.» — Salmos 56:11", a:"Identificar de quién específicamente estás esperando permiso y entender por qué esa voz pesa más que la de Dios en tu vida." },
  "Comparación":            { d:"La comparación es una de las formas más sofisticadas de idolatría — te hace medir el diseño único de Dios para tu vida contra el diseño único que Él hizo para otra. No compites con nadie porque nadie puede hacer lo que tú estás llamada a hacer.", v:"«Cada uno someta a prueba su propia obra, y entonces tendrá motivo de gloriarse solo respecto de sí mismo.» — Gálatas 6:4", a:"Entender que la comparación viene de una identidad que aún no está completamente anclada en Dios — y construirla desde ahí." },
  "Autosabotaje":           { d:"El autosabotaje casi nunca se ve como tal desde adentro. Se ve como circunstancias o mala suerte. Pero cuando el patrón se repite, el denominador común eres tú. La parte de ti que se sabotea cree que no merece el propósito que Dios le dio.", v:"«El ladrón no viene sino para hurtar y matar y destruir.» — Juan 10:10", a:"Identificar el patrón específico de sabotaje y la creencia debajo de él — esa creencia es lo que necesita ser trabajada." },
  "Mentalidad":             { d:"Una mentalidad limitante no desaparece cuando la fe llega — se transforma cuando la fe entra en contacto con el proceso de renovación mental. Puedes tener fe en Dios y seguir con una mente que opera desde la escasez y la derrota.", v:"«Transformaos por medio de la renovación de vuestro entendimiento.» — Romanos 12:2", a:"Identificar las creencias específicas que operan bajo tu superficie — las que determinan cómo te hablas cuando nadie te escucha." },
  "Perfeccionismo":         { d:"El perfeccionismo se disfraza de responsabilidad. Pero en su raíz es miedo — miedo a ser juzgada, miedo a no ser suficiente. La perfección no existe. El propósito sí. Y el propósito no espera a que estés lista.", v:"«No los que se recomiendan a sí mismos son los aprobados, sino aquellos a quienes Dios recomienda.» — 2 Corintios 10:18", a:"La creencia de que tu valor está atado a tu desempeño — y soltarla por la gracia de un Dios que te usa imperfecta." },
  "Disciplina":             { d:"La disciplina no es motivación — es un acto de fe. Es actuar en la dirección del propósito aunque no sientas nada. La mujer que espera sentirse motivada para trabajar en su llamado pone sus emociones por encima de su obediencia.", v:"«Todo lo puedo en Cristo que me fortalece.» — Filipenses 4:13", a:"Construir sistemas de disciplina que no dependan de tu estado emocional — porque el propósito requiere consistencia, no perfección." },
  "Toma de Decisiones":     { d:"La incapacidad de decidir no es falta de información — es falta de confianza en la voz de Dios dentro de ti. Cada decisión pospuesta es fe aplazada. Y la mujer que no puede decidir sola nunca podrá liderar lo que Dios le dio.", v:"«Fíate de Jehová de todo tu corazón, y no te apoyes en tu propia prudencia.» — Proverbios 3:5", a:"Aprender a distinguir la voz de Dios de la voz del miedo — y confiar en la primera aunque la segunda sea más ruidosa." },
  "Victimismo":             { d:"La diferencia entre una víctima y una mujer de propósito no es lo que le pasó — es lo que decide hacer con eso. Mientras algo o alguien sea responsable de donde estás, tú no tienes el poder de cambiar donde estás.", v:"«Todo lo puedo en Cristo que me fortalece.» — Filipenses 4:13", a:"Recuperar la agencia — la capacidad de decidir que aunque no controlaste lo que pasó, sí controlas lo que haces con ello." },
  "Soltar el Control":      { d:"Controlar es una forma de no confiar. El propósito de Dios siempre requiere soltar el control — porque si pudieras controlarlo todo, no necesitarías a Dios. La barrera del control no te mantiene segura. Te mantiene quieta.", v:"«Encomienda a Jehová tu camino, y confía en Él; y Él hará.» — Salmos 37:5", a:"Entender de dónde viene la necesidad de controlar — generalmente hay una herida o un miedo debajo que no ha sido procesado." },
  "Críticas":               { d:"La mujer cuyo propósito es visible va a ser criticada. No como excepción — como regla. Si el miedo a las críticas te mantiene escondida, tu propósito también está escondido. La pregunta no es cómo evitar las críticas — es cómo construir una identidad que no se derrumbe con ellas.", v:"«Si Dios es por nosotros, ¿quién contra nosotros?» — Romanos 8:31", a:"Construir la diferencia entre crítica que informa y crítica que hiere — y desarrollar la fortaleza para recibir la primera sin que te detenga la segunda." },
  "Inteligencia Emocional": { d:"Las emociones no son tus enemigas — son información. Pero cuando no sabes procesarlas, se convierten en el gobierno de tus decisiones. Una mujer emocionalmente reactiva no puede liderar su propósito porque cada situación difícil la moverá de su eje.", v:"«El que tarda en airarse es grande de entendimiento.» — Proverbios 14:29", a:"Desarrollar la capacidad de identificar, nombrar, y procesar tus emociones antes de que ellas tomen decisiones por ti." },
  "Perseverancia":          { d:"El propósito siempre tarda más de lo que el ego espera. La mujer que abandona cuando no ve resultados rápidos está dejando que el tiempo le diga que Dios se equivocó. La perseverancia no es aguantar pasivamente — es seguir actuando con fe activa cuando no hay evidencia visible.", v:"«No nos cansemos, pues, de hacer bien; porque a su tiempo segaremos, si no desmayamos.» — Gálatas 6:9", a:"Construir la convicción de que el llamado de Dios no se cancela por el tiempo que toma — y la disciplina de actuar sin resultados visibles." },
  "Proximidad":             { d:"El entorno más cercano es una de las barreras más silenciosas y peligrosas. No porque las personas sean malas — sino porque su miedo, su incredulidad, o su propia visión limitada puede convertirse en la voz que ahogas el llamado de Dios en ti. Una mujer rodeada del entorno equivocado puede tener toda la fe del mundo y seguir sin avanzar.", v:"«No os unáis en yugo desigual con los incrédulos; porque ¿qué compañerismo tiene la justicia con la injusticia?» — 2 Corintios 6:14", a:"Evaluar honestamente quién está en tu círculo más cercano — quién te acerca a quien Dios te llamó a ser y quién, aunque con amor, te aleja de eso." }
};

const BRG="#510100", BRG2="#3A0000", GOLD="#8C6845", G3="#CCB08A", G4="#E8D5B5", PP="#F9F5EE", PP2="#F0E9DE", INK="#1A120E";
const s = (obj) => Object.assign({}, obj);

function BCard({ name, score, rank }) {
  const [open, setOpen] = useState(rank <= 3);
  const info = INFO[name] || {};
  const prim = rank <= 3;
  const fills = [18,44,72,95];
  const lvls = ["Barrera baja","Barrera moderada","Barrera alta — trabajar pronto","Barrera crítica — prioridad inmediata"];
  const dots = ["#3B6D11","#BA7517","#BA7517","#8B1A1A"];
  return (
    <div style={{border: prim?"1px solid rgba(81,1,0,.3)":"1px solid rgba(81,1,0,.09)", borderLeft: prim?"3px solid #510100":"3px solid #CCB08A", marginBottom:10, background:"#fff"}}>
      <div onClick={()=>setOpen(!open)} style={{display:"flex",alignItems:"center",gap:12,padding:"13px 15px",cursor:"pointer"}}>
        <div style={{fontFamily:"Georgia,serif",fontSize:24,fontWeight:300,color:prim?BRG:G3,minWidth:32,opacity:.7,lineHeight:1}}>{String(rank).padStart(2,"0")}</div>
        <div style={{flex:1}}>
          <div style={{fontFamily:"Georgia,serif",fontSize:16,fontWeight:500,color:BRG,marginBottom:3}}>{name}</div>
          <div style={{display:"flex",alignItems:"center",gap:5,marginBottom:5}}>
            <div style={{width:6,height:6,borderRadius:"50%",background:dots[score-1]}}/>
            <span style={{fontSize:10,color:"#9A8878",letterSpacing:".07em"}}>{lvls[score-1]}</span>
          </div>
          <div style={{width:"100%",height:3,background:"rgba(81,1,0,.08)",borderRadius:2}}>
            <div style={{height:"100%",width:fills[score-1]+"%",background:prim?BRG:G3,borderRadius:2}}/>
          </div>
        </div>
        <span style={{fontSize:11,color:"#9A8878",display:"inline-block",transform:open?"rotate(90deg)":"none",transition:"transform .2s"}}>&#9654;</span>
      </div>
      {open && (
        <div style={{borderTop:"1px solid rgba(81,1,0,.07)",padding:"13px 15px"}}>
          <p style={{fontSize:13,lineHeight:1.8,color:"#5A4030",marginBottom:12}}>{info.d}</p>
          <div style={{fontFamily:"Georgia,serif",fontSize:13,fontStyle:"italic",color:BRG,padding:"9px 13px",background:"rgba(81,1,0,.04)",borderLeft:"2px solid #510100",marginBottom:10,lineHeight:1.55}}>{info.v}</div>
          <div style={{fontSize:12,color:"#5A4030",padding:"9px 11px",background:PP2,lineHeight:1.65}}>
            <strong style={{display:"block",fontSize:9,letterSpacing:".12em",textTransform:"uppercase",color:BRG,marginBottom:4}}>Qué necesitas trabajar</strong>
            {info.a}
          </div>
        </div>
      )}
    </div>
  );
}

export default function App() {
  useEffect(() => {
    const link = document.createElement("link");
    link.href = "https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;500&display=swap";
    link.rel = "stylesheet";
    document.head.appendChild(link);
  }, []);
  const [screen, setScreen] = useState("cover");
  const [qi, setQi] = useState(0);
  const [ans, setAns] = useState({});

  const cur = Q[qi];
  const pct = Math.round((qi/Q.length)*100);
  const letters = ["A","B","C","D"];

  const doStart = () => { setScreen("q"); setQi(0); setAns({}); };
  const doSelect = (v) => setAns(prev=>({...prev,[qi]:v}));
  const doNext = () => {
    if(!ans[qi]) return;
    if(qi < Q.length-1){ setQi(qi+1); }
    else { setScreen("loading"); setTimeout(()=>setScreen("results"),3200); }
  };
  const doBack = () => { if(qi>0) setQi(qi-1); };
  const doRestart = () => { setScreen("cover"); setQi(0); setAns({}); };

  const sorted = [...Q].map((q,i)=>({name:q.b, score:ans[i]||2})).sort((a,b)=>b.score-a.score);
  const top = sorted[0];
  const highCt = sorted.filter(b=>b.score>=3).length;

  if(screen==="cover") return (
    <div style={{background:BRG2,minHeight:"100vh",display:"flex",flexDirection:"column",alignItems:"center",justifyContent:"center",textAlign:"center",padding:"3rem 1.5rem",position:"relative",overflow:"hidden"}}>
      <div style={{position:"absolute",width:500,height:500,borderRadius:"50%",border:"1px solid rgba(204,176,138,.05)",top:-180,right:-180,pointerEvents:"none"}}/>
      <p style={{fontFamily:"'Cormorant Garamond', Georgia, serif",fontSize:"clamp(16px,4vw,24px)",fontWeight:400,fontStyle:"normal",textTransform:"uppercase",color:"#E8D5B5",letterSpacing:".25em",marginBottom:"1.5rem",position:"relative",zIndex:1}}>La Mujer Que Nací Para Ser</p>
      <p style={{fontSize:10,letterSpacing:".3em",textTransform:"uppercase",color:G3,opacity:.6,marginBottom:"1rem",position:"relative",zIndex:1}}>Diagnóstico gratuito · Maribella Nivar</p>
      <h1 style={{fontFamily:"Georgia,serif",fontSize:"clamp(30px,6vw,52px)",fontWeight:300,color:PP,lineHeight:1.1,marginBottom:".75rem",maxWidth:560,position:"relative",zIndex:1}}>
        Descubre las Barreras que <em style={{color:G4}}>Bloquean Tu Propósito</em>
      </h1>
      <div style={{width:32,height:1,background:"rgba(204,176,138,.28)",margin:"1.25rem auto",position:"relative",zIndex:1}}/>
      <p style={{fontSize:13,color:"rgba(249,245,238,.48)",maxWidth:420,lineHeight:1.85,marginBottom:"2.5rem",position:"relative",zIndex:1}}>15 preguntas que revelan exactamente qué está deteniendo a la mujer que Dios diseñó en ti.</p>
      <button onClick={doStart} style={{background:GOLD,color:PP,border:"none",padding:"14px 40px",fontSize:11,letterSpacing:".2em",textTransform:"uppercase",fontWeight:500,cursor:"pointer",position:"relative",zIndex:1,fontFamily:"inherit",borderRadius:1}}>
        Comenzar el diagnóstico
      </button>
      <p style={{fontSize:10,color:"rgba(249,245,238,.22)",marginTop:"1rem",letterSpacing:".06em",position:"relative",zIndex:1}}>5 minutos · Completamente gratis · Resultados inmediatos</p>
    </div>
  );

  if(screen==="q") return (
    <div style={{background:PP,minHeight:"100vh",display:"flex",flexDirection:"column"}}>
      <div style={{position:"sticky",top:0,zIndex:10,background:"rgba(249,245,238,.97)",backdropFilter:"blur(12px)",borderBottom:"1px solid rgba(81,1,0,.09)",padding:".7rem 1.5rem",display:"flex",alignItems:"center",gap:12}}>
        <span style={{fontFamily:"'Cormorant Garamond', Georgia, serif",fontSize:12,fontStyle:"normal",textTransform:"uppercase",color:"rgba(249,245,238,.45)",letterSpacing:".18em",whiteSpace:"nowrap"}}>La Mujer Que Nací Para Ser</span>
        <div style={{flex:1,height:3,background:"rgba(81,1,0,.1)",borderRadius:2}}>
          <div style={{height:"100%",width:pct+"%",background:BRG,borderRadius:2,transition:"width .4s ease"}}/>
        </div>
        <span style={{fontSize:10,color:"#9A8878",letterSpacing:".08em",whiteSpace:"nowrap"}}>{qi+1} de {Q.length}</span>
      </div>
      <div style={{flex:1,maxWidth:640,margin:"0 auto",padding:"2.5rem 1.5rem 2rem",width:"100%"}}>
        <div style={{fontSize:9,letterSpacing:".26em",textTransform:"uppercase",color:GOLD,fontWeight:500,marginBottom:".5rem"}}>{cur.b}</div>
        <div style={{fontFamily:"Georgia,serif",fontSize:13,color:"rgba(81,1,0,.12)",lineHeight:1,marginBottom:".15rem"}}>{String(qi+1).padStart(2,"0")}</div>
        <h2 style={{fontFamily:"Georgia,serif",fontSize:"clamp(18px,3.5vw,25px)",fontWeight:400,color:BRG,lineHeight:1.25,marginBottom:".5rem"}}>{cur.t}</h2>
        <p style={{fontSize:12,color:"#9A8878",fontStyle:"italic",marginBottom:"1.5rem",lineHeight:1.65}}>{cur.s}</p>
        <div style={{display:"flex",flexDirection:"column",gap:10}}>
          {cur.o.map((opt,i)=>(
            <div key={i} onClick={()=>doSelect(i+1)} style={{display:"flex",alignItems:"flex-start",gap:12,padding:"11px 13px",border:ans[qi]===i+1?"1px solid #510100":"1px solid rgba(81,1,0,.09)",background:ans[qi]===i+1?"rgba(81,1,0,.04)":"#fff",cursor:"pointer",borderRadius:1,transition:"all .15s"}}>
              <div style={{width:22,height:22,minWidth:22,borderRadius:"50%",border:ans[qi]===i+1?"none":"1px solid rgba(81,1,0,.2)",background:ans[qi]===i+1?BRG:"transparent",display:"flex",alignItems:"center",justifyContent:"center",fontSize:10,fontWeight:500,color:ans[qi]===i+1?PP:"#9A8878",flexShrink:0}}>
                {letters[i]}
              </div>
              <span style={{fontSize:13,lineHeight:1.6,color:ans[qi]===i+1?INK:"#5A4030"}}>{opt}</span>
            </div>
          ))}
        </div>
        <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginTop:"1.75rem"}}>
          {qi>0 ? <button onClick={doBack} style={{background:"none",border:"1px solid rgba(81,1,0,.15)",padding:"8px 18px",fontSize:10,letterSpacing:".14em",textTransform:"uppercase",color:"#9A8878",cursor:"pointer",fontFamily:"inherit",borderRadius:1}}>← Anterior</button> : <span/>}
          <button onClick={doNext} style={{background:ans[qi]?BRG:"rgba(81,1,0,.18)",border:"none",padding:"10px 22px",fontSize:10,letterSpacing:".17em",textTransform:"uppercase",fontWeight:500,color:PP,cursor:ans[qi]?"pointer":"default",fontFamily:"inherit",borderRadius:1,transition:"background .2s"}}>
            {qi===Q.length-1?"Ver mis resultados →":"Siguiente →"}
          </button>
        </div>
      </div>
    </div>
  );

  if(screen==="loading") return (
    <div style={{background:BRG2,minHeight:"100vh",display:"flex",flexDirection:"column",alignItems:"center",justifyContent:"center",textAlign:"center",padding:"3rem 1.5rem"}}>
      <p style={{fontFamily:"'Cormorant Garamond', Georgia, serif",fontSize:"clamp(14px,4vw,20px)",fontWeight:400,fontStyle:"normal",textTransform:"uppercase",color:"#E8D5B5",letterSpacing:".25em",marginBottom:"2rem"}}>La Mujer Que Nací Para Ser</p>
      <p style={{fontFamily:"Georgia,serif",fontSize:22,fontStyle:"italic",fontWeight:300,color:PP,marginBottom:"1rem"}}>Analizando tus barreras…</p>
      <div style={{width:200,height:2,background:"rgba(255,255,255,.1)",borderRadius:2,margin:".75rem auto"}}>
        <div style={{height:"100%",width:"100%",background:G3,borderRadius:2,transition:"width 2.8s ease"}}/>
      </div>
      <p style={{fontSize:11,color:"rgba(249,245,238,.35)",letterSpacing:".1em",marginTop:".75rem"}}>Preparando tu diagnóstico personalizado</p>
    </div>
  );

  return (
    <div style={{background:PP,minHeight:"100vh"}}>
      <div style={{background:BRG2,padding:"4rem 1.5rem 3rem",textAlign:"center",position:"relative",overflow:"hidden"}}>
        <div style={{position:"absolute",width:400,height:400,borderRadius:"50%",border:"1px solid rgba(204,176,138,.05)",top:-150,right:-120,pointerEvents:"none"}}/>
        <p style={{fontSize:9,letterSpacing:".28em",textTransform:"uppercase",color:G3,opacity:.6,marginBottom:".75rem",position:"relative",zIndex:1}}>Tu diagnóstico personal</p>
        <h2 style={{fontFamily:"Georgia,serif",fontSize:"clamp(22px,5vw,38px)",fontWeight:300,color:PP,lineHeight:1.15,marginBottom:".75rem",position:"relative",zIndex:1}}>
          Tu barrera principal es <em style={{color:G4}}>{top&&top.name}</em><br/>— y no está sola
        </h2>
        <p style={{fontSize:13,color:"rgba(249,245,238,.5)",maxWidth:460,margin:"0 auto",lineHeight:1.8,position:"relative",zIndex:1}}>Identificamos {highCt} barreras con intensidad alta. Aquí está tu diagnóstico completo, ordenado de la más intensa a la menos intensa.</p>
      </div>
      <div style={{maxWidth:660,margin:"0 auto",padding:"2rem 1.25rem"}}>
        <p style={{fontSize:9,letterSpacing:".26em",textTransform:"uppercase",color:GOLD,fontWeight:500,marginBottom:"1.25rem",textAlign:"center"}}>Tus barreras — de mayor a menor intensidad</p>
        {sorted.map((b,i)=><BCard key={b.name} name={b.name} score={b.score} rank={i+1}/>)}
      </div>
      <div style={{background:BRG,padding:"3rem 1.5rem",textAlign:"center"}}>
        <p style={{fontSize:10,letterSpacing:".4em",color:"rgba(204,176,138,.28)",marginBottom:"1.5rem"}}>✦  ✦  ✦</p>
        <h3 style={{fontFamily:"Georgia,serif",fontSize:"clamp(20px,4vw,32px)",fontWeight:300,color:PP,lineHeight:1.2,marginBottom:"1rem"}}>Lo que este diagnóstico vino a <em style={{color:G4,opacity:.88}}>decirte</em></h3>
        <p style={{fontSize:13.5,lineHeight:1.95,color:"rgba(249,245,238,.6)",maxWidth:480,margin:"0 auto 1rem"}}>Las barreras que identificaste no son defectos. Son patrones. Y los patrones se pueden trabajar — con un proceso específico que va desde la raíz.</p>
        <p style={{fontSize:13.5,lineHeight:1.95,color:"rgba(249,245,238,.6)",maxWidth:480,margin:"0 auto"}}>Eso es exactamente lo que hace <strong style={{color:PP}}>La Mujer Que Nací Para Ser.</strong></p>
      </div>
      <div style={{background:PP2,padding:"3rem 1.5rem"}}>
        <div style={{maxWidth:540,margin:"0 auto"}}>
          <p style={{fontSize:9,letterSpacing:".26em",textTransform:"uppercase",color:GOLD,marginBottom:".75rem",textAlign:"center"}}>El siguiente paso</p>
          <h3 style={{fontFamily:"Georgia,serif",fontSize:"clamp(20px,4vw,30px)",fontWeight:300,color:BRG,lineHeight:1.15,marginBottom:"1rem",textAlign:"center"}}>El proceso que trabaja exactamente <em>estas barreras</em></h3>
          <p style={{fontSize:13,lineHeight:1.9,color:"#5A4030",marginBottom:"1.75rem",textAlign:"center"}}>Este diagnóstico te mostró el qué. El programa te da el cómo.</p>
          <div style={{background:INK,padding:"2rem"}}>
            <p style={{fontSize:8.5,letterSpacing:".22em",textTransform:"uppercase",color:G3,opacity:.6,marginBottom:".75rem"}}>El Programa</p>
            <p style={{fontFamily:"Georgia,serif",fontSize:20,fontStyle:"italic",fontWeight:300,color:PP,marginBottom:"1.5rem",lineHeight:1.3}}>La Mujer Que Nací Para Ser</p>
            {["15 módulos que trabajan cada barrera que este test reveló","Identidad, mentalidad y propósito desde la raíz","Sanación emocional — no solo inspiración","Disciplina, perseverancia y carácter de la mujer llamada","Activación real del propósito — con proceso, no con espera","Acceso inmediato y de por vida"].map((f,i)=>(
              <div key={i} style={{display:"flex",gap:10,padding:"8px 0",borderBottom:"1px solid rgba(255,255,255,.05)",fontSize:12,color:"rgba(249,245,238,.5)",alignItems:"flex-start"}}>
                <span style={{color:GOLD,fontSize:9,marginTop:3,flexShrink:0}}>—</span>{f}
              </div>
            ))}
            <div style={{fontSize:60,fontFamily:"Georgia,serif",fontWeight:300,color:G4,lineHeight:1,marginTop:"1.5rem",marginBottom:4}}>$79</div>
            <div style={{fontSize:10,color:"rgba(249,245,238,.22)",letterSpacing:".08em",marginBottom:"1.5rem"}}>Inversión única · Acceso inmediato · Acceso de por vida</div>
            <a href="https://www.maribellanivar.com/programa" style={{display:"block",background:GOLD,color:PP,padding:"13px 1rem",fontSize:10,letterSpacing:".2em",textTransform:"uppercase",fontWeight:500,textAlign:"center",textDecoration:"none",fontFamily:"inherit",borderRadius:1}}>
              Quiero trabajar estas barreras — $79
            </a>
          </div>
          <p style={{fontSize:10.5,color:"#9A8878",marginTop:".9rem",textAlign:"center"}}>¿Tienes preguntas? Escríbele a Maribella: <strong>lamujerquenaciparaser@gmail.com</strong></p>
          <p style={{fontFamily:"Georgia,serif",fontSize:15,fontStyle:"italic",color:"#9A8878",textAlign:"center",marginTop:"1.5rem"}}>— att. Maribella</p>
          <div style={{textAlign:"center",marginTop:"1.25rem"}}>
            <button onClick={doRestart} style={{background:"none",border:"1px solid rgba(81,1,0,.15)",padding:"8px 20px",fontSize:10,letterSpacing:".13em",textTransform:"uppercase",color:"#9A8878",cursor:"pointer",fontFamily:"inherit",borderRadius:1}}>Volver a hacer el test</button>
          </div>
        </div>
      </div>
    </div>
  );
}
