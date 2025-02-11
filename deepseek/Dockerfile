FROM ollama-base:latest


COPY scripts/start.sh /usr/local/bin/

RUN chmod +x /usr/local/bin/start.sh
RUN mkdir -p /root/.ollama

RUN ollama serve & \
    SERVER_PID=$! && \
    sleep 5 && \
    ollama pull deepseek-coder:latest && \
    kill $SERVER_PID && \
    sleep 2 

EXPOSE 11434

CMD ["/usr/local/bin/start.sh"]