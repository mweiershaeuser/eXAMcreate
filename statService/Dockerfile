FROM lukechannings/deno:v1.34.3

EXPOSE 8000

WORKDIR /app

USER deno

COPY deps.ts deno.lock ./
RUN deno cache --lock=deno.lock deps.ts

COPY . .
RUN deno cache main.ts

ENV EXAMMANAGE_BACKEND_URL="http://localhost:8080"
CMD ["run", "--lock=deno.lock", "--allow-net", "--allow-env", "main.ts"]