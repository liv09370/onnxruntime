require "bundler/gem_tasks"
require "rake/testtask"

task default: :test
Rake::TestTask.new do |t|
  t.libs << "test"
  t.pattern = "test/**/*_test.rb"
end

shared_libraries = %w(libonnxruntime.so libonnxruntime.dylib onnxruntime.dll)

# ensure vendor files exist
task :ensure_vendor do
  shared_libraries.each do |file|
    raise "Missing file: #{file}" unless File.exist?("vendor/#{file}")
  end
end

Rake::Task["build"].enhance [:ensure_vendor]

def version
  "1.5.2"
end

def download_official(library, remote_lib, file)
  require "fileutils"
  require "open-uri"
  require "tmpdir"

  url = "https://github.com/microsoft/onnxruntime/releases/download/v#{version}/#{file}"
  puts "Downloading #{file}..."
  dir = Dir.mktmpdir
  Dir.chdir(dir) do
    File.binwrite(file, URI.open(url).read)
    command = file.end_with?(".zip") ? "unzip" : "tar xf"
    system "#{command} #{file}"
    path = "#{dir}/#{file[0..-5]}/lib/#{remote_lib}"
    FileUtils.cp(path, File.expand_path("vendor/#{library}", __dir__))
    puts "Saved vendor/#{library}"
  end
end

def download_file(file)
  require "open-uri"

  url = "https://github.com/ankane/ml-builds/releases/download/onnxruntime-#{version}/#{file}"
  puts "Downloading #{file}..."
  dest = "vendor/#{file}"
  File.binwrite(dest, URI.open(url).read)
  puts "Saved #{dest}"
end

# https://github.com/microsoft/onnxruntime/releases
namespace :vendor do
  task :linux do
    download_official("libonnxruntime.so", "libonnxruntime.so.#{version}", "onnxruntime-linux-x64-#{version}.tgz")
  end

  task :mac do
    download_official("libonnxruntime.dylib", "libonnxruntime.#{version}.dylib", "onnxruntime-osx-x64-#{version}.tgz")
  end

  task :windows do
    # OpenMP disabled to prevent segmentation fault
    # download_file("onnxruntime.dll")
    download_official("onnxruntime.dll", "onnxruntime.dll", "onnxruntime-win-x64-#{version}.zip")
  end

  task all: [:linux, :mac, :windows]
end
