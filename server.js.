import express from "express";
import dotenv from "dotenv";
dotenv.config();
const app=express();app.use(express.json({limit:"1mb"}));app.use(express.static("public"));
app.post("/api/generate",async(req,res)=>{
 const {prompt,type,name}=req.body||{};
 if(!prompt||typeof prompt!=="string")return res.status(400).json({error:"Escreve a ideia do jogo."});
 if(!process.env.OPENAI_API_KEY)return res.status(503).json({error:"OPENAI_API_KEY não configurada no servidor."});
 try{
 const r=await fetch("https://api.openai.com/v1/responses",{method:"POST",headers:{"Authorization":`Bearer ${process.env.OPENAI_API_KEY}`,"Content-Type":"application/json"},body:JSON.stringify({model:process.env.OPENAI_MODEL||"gpt-4.1-mini",input:[{role:"system",content:"És especialista em design de jogos 3D. Responde em português com JSON válido: summary (frase curta), description (descrição visual detalhada do cenário), steps (array de sugestões). Não alegues ter criado um jogo completo."},{role:"user",content:`Projeto ${name||"jogo"}; género ${type||"mundo aberto"}; ideia: ${prompt}`}],text:{format:{type:"json_object"}}})});
 const data=await r.json();if(!r.ok)return res.status(r.status).json({error:data.error?.message||"Falha na API"});const out=data.output?.flatMap(v=>v.content||[]).find(v=>v.type==="output_text")?.text;if(!out)return res.status(502).json({error:"Resposta IA vazia"});res.json(JSON.parse(out));
 }catch(e){res.status(500).json({error:e.message})}
});
app.listen(process.env.PORT||3000,()=>console.log("GAME AI STUDIO online"));
