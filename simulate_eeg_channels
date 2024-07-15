% FUNCTION NAME: simulate_eeg_channels
%
% DESCRIPTION:
% This function simulates 18 EEG channels where there is synchrony for some pairs of channels.
% This synchrony occurs with some phase delay since a given signal takes time to go from one cortical area to another.
% Each channel is a non-stationary, non-linear time series.

% Define the 18 EEG channels based on the 10/20 system
channels = {'Fp1', 'Fp2', 'F7', 'F3', 'Fz', 'F4', 'F8', 'T3', 'C3', 'Cz', 'C4', 'T4', 'T5', 'P3', 'Pz', 'P4', 'O1', 'O2'};

% Time specifications
Fs = 256; % Sampling frequency in Hz
dt = 1/Fs; % Time step
T = 10; % Total time in seconds
t = 0:dt:T-dt; % Time vector

% Initialize the EEG data matrix
EEG = zeros(length(channels), length(t));

% Generate non-stationary, non-linear signals for each channel
for i = 1:length(channels)
    % Create a non-stationary, non-linear signal
    EEG(i, :) = 0.5*sin(2*pi*0.5*t + rand*2*pi) + 0.3*sin(2*pi*1.5*t + rand*2*pi) + 0.2*sin(2*pi*3*t + rand*2*pi) + 0.1*randn(size(t));
end

% Introduce synchrony with phase delay between specific pairs of channels
synchrony_pairs = [1, 2; 3, 4; 5, 6; 7, 8; 9, 10]; % Pairs of channels to synchronize
phase_delays = [0, 0, 0.3, 0.4, 0.5]; % Phase delays in seconds

for k = 1:size(synchrony_pairs, 1)
    ch1 = synchrony_pairs(k, 1);
    ch2 = synchrony_pairs(k, 2);
    delay_samples = round(phase_delays(k) * Fs);
    
    % Apply phase delay to the second channel in the pair
    EEG(ch2, delay_samples+1:end) = EEG(ch1, 1:end-delay_samples);
end

% Plot the generated EEG signals
figure;
for i = 1:length(channels)
    subplot(length(channels), 1, i);
    plot(t, EEG(i, :));
    title(['Channel ' channels{i}]);
    xlabel('Time (s)');
    ylabel('Amplitude');
end

% Save the EEG data to a .mat file
save('synthetic1_EEG.mat', 'EEG', 'channels', 'Fs', 't');
