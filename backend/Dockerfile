# Use the uv base image with Python and uv preinstalled
FROM ghcr.io/astral-sh/uv:alpine

# Set the env variable to enable logs
ENV PYTHONUNBUFFERED=1

# Set the working directory in the container
WORKDIR /usr/local/app

# Copy the dependencie files (leverage docker laayer caching to avoid re-installing dependencies on every code change)
COPY pyproject.toml uv.lock ./

# Install required packages
RUN uv sync

# Copy the source code
COPY ./ ./

# Grant access to the container's port 8000
EXPOSE 8000

# Start the server
CMD ["uv", "run", "python", "manage.py", "runserver", "0.0.0.0:8000"]
